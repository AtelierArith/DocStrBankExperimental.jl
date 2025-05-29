```
GBMMfit(HistoricalData, PeriodsToForecast; rng="none")
```

GBMMfit uses a vector of historical data to calculate the log returns and use the mean and standard deviation to project a random walk. It the uses the last datapoint in the set as the starting point for the new forecast.

**HistoricalData**: Vector containing historical data

**PeriodsToForecast**: integer >1

**rng** is fully random when set to none. You can specify the rng you want to seed the results e.g. MersenneTwister(1234)
