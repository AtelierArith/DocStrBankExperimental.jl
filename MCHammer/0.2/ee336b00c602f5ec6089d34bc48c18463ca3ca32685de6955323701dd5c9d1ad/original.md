```
GBMM(LastValue, ReturnsMean, ReturnsStd, PeriodsToForecast; rng::Any="none")
```

GBMM produces a random walk using the last data point and requires a mean and standard deviation to be provided.

**LastValue**: The most recent data point on which to base your random walk.

**ReturnsMean and ReturnsStd** : Historical Mean and Standard Deviation of Returns

**PeriodsToForecast** is an integer >1

**rng** is fully random when set to none. You can specify the rng you want to seed the results e.g. MersenneTwister(1234)
