```
variance_lat(var; ignore_nan = true, corrected = true)
```

Return a new OutputVar where the values are the variances along the latitude dimension.

If `corrected` is `true`, then the variance is computed by dividing the sample mean by `n - 1`, whereas if `corrected` is `false`, then the variance is computed by dividing the sample mean by `n`, where `n` is the number of elements that the variance is being computed over.
