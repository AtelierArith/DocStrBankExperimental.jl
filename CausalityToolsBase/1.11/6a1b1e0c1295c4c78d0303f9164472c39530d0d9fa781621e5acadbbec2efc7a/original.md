```
optimal_dimension(v; dims = 2:8,
    method_dimension = "fnn", method_delay = "first_min")
```

Estimate the optimal embedding dimension for `v` by first estimating the optimal lag, then using that lag to estimate the dimension.

## Arguments

  * **`v`**: The data series for which to estimate the embedding dimension.
  * **`dims`**: The dimensions to try
