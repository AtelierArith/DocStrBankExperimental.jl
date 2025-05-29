```
rearrange(
    cm::CovarianceMatrix,
    labels::Vector{Symbol},
    time_period_per_unit::Union{Missing,Dates.Period} = cm.time_period_per_unit,
)
```

Rearrange the order of labels in a `CovarianceMatrix`.

### Takes

  * `cm` - A `CovarianceMatrix`.
  * `labels` - A `Vector` of labels.
  * `time_period_per_unit` - The time period you want for the resultant Covariance Matrix

### Returns

  * A `CovarianceMatrix`.
