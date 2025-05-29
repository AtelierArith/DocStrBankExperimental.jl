```
covariance(
    cm::CovarianceMatrix,
    period::Dates.Period = cm.time_period_per_unit,
    assets::Vector{Symbol} = cm.labels,
)
```

This makes a `Hermitian` matrix for the covariance matrix over some duration.

### Inputs

  * `cm` - A `CovarianceMatrix` struct.
  * `period` - A duration for which you want a covariance matrix. This should be in a Dates.Period.
  * `assets` - What assets in include in the covariance matrix.

### Returns

  * A `Hermitian`. The labelling of assets for each row/column is as per the input `assets` vector.
