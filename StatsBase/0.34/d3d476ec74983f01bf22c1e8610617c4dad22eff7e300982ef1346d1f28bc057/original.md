```
StatsBase.mad!(x; center=median!(x), normalize=true)
```

Compute the median absolute deviation (MAD) of array `x` around `center` (by default, around the median), overwriting `x` in the process.

If `normalize` is set to `true`, the MAD is multiplied by `1 / quantile(Normal(), 3/4) ≈ 1.4826`, in order to obtain a consistent estimator of the standard deviation under the assumption that the data is normally distributed.
