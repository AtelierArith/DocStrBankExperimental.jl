```
make_nan_covariance_matrix(
    labels::Vector{Symbol},
    time_period_per_unit::Dates.Period,
)
```

This makes an empty `CovarianceMatrix` struct with all volatilities and correlations being NaNs.

### Inputs

  * `labels` - The names of the asset names for this (empty) `CovarianceMatrix`.
  * `time_period_per_unit` - The time interval the volatilities will be for.

### Returns

  * An (empty) `CovarianceMatrix`
