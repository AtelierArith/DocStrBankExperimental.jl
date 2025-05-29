```
QuantileMetric <: AbstractMetric
```

QuantileMetric is a metric descriptor for quantile data. It is based on the quantiles of the data and their corresponding values.

## Fields

  * `size::Int`: The size of the dataset.
  * `levels::Vector{Float64}`: The quantile levels (e.g. 0.25, 0.5, 0.75).
  * `values::Vector{Float64}`: The corresponding values for the quantile levels.
  * `skip_nan::Bool`: If `true``, NaN values are allowed in simulated data and will be ignored. If`false`, NaN values are not allowed.
  * `cov_inv::Matrix{Float64}`: The inverse of the covariance matrix of the groups.
  * `group_active::Vector{Bool}`: A boolean vector indicating which groups are active (non-zero rates).
  * `rates::Vector{Float64}`: The probabilities of each group.

## Constructor

  * `QuantileMetric(size::Int, levels::Vector{Float64}, values::Vector{Float64}; skip_nan::Bool = false)`: Creates a new instance of QuantileMetric.  It validates the input data and calculates the inverse covariance matrix.
