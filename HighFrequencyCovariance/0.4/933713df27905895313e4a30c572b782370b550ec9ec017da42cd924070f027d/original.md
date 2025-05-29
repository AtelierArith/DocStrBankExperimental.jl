```
calculate_mean_abs_distance_covar(
    cov1::CovarianceMatrix,
    cov2::CovarianceMatrix,
    decimal_places::Integer = 8;
    return_nans_if_symbols_dont_match::Bool = true,
)
```

Calculates the mean absolute distance (elementwise in L1 norm) between the covariance matrices (over the natural time unit) of two `CovarianceMatrix`s. Undefined if any labels differ between the two `CovarianceMatrix`s.

Note that this is different from calculate*mean*abs_distance in that this function returns one real for the distance between actual covariance matrices rather than a tuple showing the distances in terms of correlation and volatility.

### Inputs

  * `cov1` - The first `CovarianceMatrix`
  * `cov2` - The second `CovarianceMatrix`
  * `decimal_places` - How many decimal places to show the result to.
  * `return_nans_if_symbols_dont_match` - If the symbols don't match should it be an error. Or if false we only compare common symbols in both `CovarianceMatrix`s

### Returns

  * A Real
