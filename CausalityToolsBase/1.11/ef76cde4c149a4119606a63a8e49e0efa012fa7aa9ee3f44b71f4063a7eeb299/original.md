```
optimal_delay(v; method = "mi_min")
```

Estimate the optimal embedding lag for `v`. 

## Keyword arguments

  * **`method`**: Either "fnn" (Kennel's false nearest neighbors method).    Default is `mi_min`.
  * **`τs`**: The lags over which to estimate the embedding lag. Defaults to 10% of the    length of the time series.
