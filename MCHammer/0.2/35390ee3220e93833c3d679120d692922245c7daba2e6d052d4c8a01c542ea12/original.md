```
fit_stats(SampleData; DistFit=[], pvals=true, Increment=0.1)
```

Calculates descriptive statistics for the sample data and for each fitted distribution in `DistFit`.

# Arguments

  * `SampleData`: Array of sample data.
  * `DistFit` (optional): Pre-selected array of distribution types to fit.   Defaults to `[Normal, LogNormal, Uniform]` if not provided.
  * `pvals` (optional): Displays percentiles for the sample data and the fits
  * `Increment` (optional): Increment for the percentiles (e.g., 0.1 for 0%, 10%, …, 100%).   Default is 0.1.

# Returns

A DataFrame (transposed) containing descriptive statistics (mean, median, mode, std, variance, skewness, kurtosis, etc.)  for the sample data and for each fitted distribution.

When `pvals = true` percentiles are added the to stats table

  * `Percentile`: The percentile (in %).
  * `SampleData`: The corresponding quantile of the sample data.
  * One column per fitted distribution containing the theoretical quantiles.
