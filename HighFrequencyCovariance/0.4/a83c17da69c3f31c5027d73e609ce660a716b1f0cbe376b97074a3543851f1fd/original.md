```
calculate_mean_abs_distance(
    cov1::CovarianceMatrix,
    cov2::CovarianceMatrix,
    decimal_places::Integer = 8;
    return_nans_if_symbols_dont_match::Bool = true,
)
```

Calculates the mean absolute distance (elementwise in L1 norm) between two `CovarianceMatrix`s. Undefined if any labels differ between the two `CovarianceMatrix`s.

### Inputs

  * `cov1` - The first `CovarianceMatrix`
  * `cov2` - The second `CovarianceMatrix`
  * `decimal_places` - How many decimal places to show the result to.
  * `return_nans_if_symbols_dont_match` - If the symbols don't match should it be an error. Or if false we only compare common symbols in both `CovarianceMatrix`s

### Returns

  * An `Tuple` with the distance for correlations in first entry and distance for volatilities in the second.

    calculate*mean*abs_distance(d1::Dict{Symbol,<:Real}, d2::Dict{Symbol,<:Real})

Calculates the mean absolute distance (elementwise in L1 norm) between two `CovarianceMatrix`s.

### Inputs

  * `d1` - The first `Dict`
  * `d2` - The second `Dict`

### Returns

  * A scalar with the mean distance between matching elements.
