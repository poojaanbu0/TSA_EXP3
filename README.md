### Reg.No:212222240072
### Date  : 14/03/25
# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
data = pd.read_csv("/content/seattle_weather_1948-2017.csv")  # replace "weather_data.csv" with your actual file name

# Convert the 'DATE' column to datetime format
data['DATE'] = pd.to_datetime(data['DATE'])

# Select the temperature data ('TMAX') as the time series data
time_series = data['TMAX'] 
```
```
# Parameters for the ACF calculation
n_data_points = len(time_series)
n_lags = min(35, n_data_points - 1)
acf_values = np.zeros(n_lags)

# Calculate the mean and variance of the time series
mean = np.mean(time_series)
variance = np.var(time_series)

# Normalize the time series by subtracting the mean
normalized_data = time_series - mean

# Compute ACF manually
for lag in range(n_lags):
    lagged_data = np.roll(normalized_data, -lag)
    acf_values[lag] = np.sum(normalized_data[:n_data_points-lag] * lagged_data[:n_data_points-lag]) / (variance * (n_data_points - lag))

# Plot the ACF values
plt.figure(figsize=(10, 6))
plt.stem(range(n_lags), acf_values)
plt.title(f'ACF Plot (Manual Calculation, Lags: {n_lags})')
plt.xlabel('Lag')
plt.ylabel('ACF')
plt.show()

```
### OUTPUT:
![image](https://github.com/user-attachments/assets/2bdd6f4f-cd26-4e5a-be29-b412c89b7e28)



### RESULT:
 Thus, the python code for implementing the auto correlation function is executed successfully.
