```
OneTimescaleWithMissing
```

Module for handling time series analysis with missing data. Uses specialized methods for handling NaN values:

  * For ACF: Uses comp*ac*time_missing (equivalent to statsmodels.tsa.statstools.acf with missing="conservative")
  * For PSD: Uses Lomb-Scargle periodogram to handle irregular sampling
