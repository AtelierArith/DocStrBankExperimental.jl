```
std_error(x[; method])
```

Estimate the standard error of the mean of the given time series.

The keyword `method` can be used to choose one out of the following methods:

  * Logarithmic binning: `:log` (default)
  * Full binning: `:full`
  * Jackknife resampling: `:jackknife`
