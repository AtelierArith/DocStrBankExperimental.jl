```
OneTimescaleAndOscWithMissing
```

Module for handling time series analysis with both oscillations and missing data. Uses specialized methods for handling NaN values:

  * For ACF: Uses comp*ac*time_missing for proper handling of gaps
  * For PSD: Uses Lomb-Scargle periodogram for irregular sampling
