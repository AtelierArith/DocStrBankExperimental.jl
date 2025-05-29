```
MAD, median = mad(x)
```

Compute the median absolute deviation (MAD) of collection `x` around the median

The MAD is multiplied by `1 / quantile(Normal(), 3/4) ≈ 1.4826`, in order to obtain a consistent estimator of the standard deviation under the assumption that the data is normally distributed. Return also the median of `x` (used to compute the MAD) as a second output.
