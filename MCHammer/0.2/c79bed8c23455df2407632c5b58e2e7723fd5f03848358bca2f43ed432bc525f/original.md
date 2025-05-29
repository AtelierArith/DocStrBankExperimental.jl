```
GBMM_Sim(LastValue, ReturnsMean, ReturnsStd, PeriodsToForecast; trials=1)
```

GBMM_Sim produces multiple random walks using the last data point and requires a mean and standard deviation to be provided.

**LastValue**: The most recent data point on which to base your random walk.

**ReturnsMean and ReturnsStd** : Historical Mean and Standard Deviation of Returns

**PeriodsToForecast** is an integer >1

**trials**: is to produce a simulated time-series array.
