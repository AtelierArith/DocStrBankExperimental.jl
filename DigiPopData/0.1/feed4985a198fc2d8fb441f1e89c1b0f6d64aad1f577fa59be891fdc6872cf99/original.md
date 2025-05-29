```
CategoryMetric <: AbstractMetric
```

CategoryMetric is a metric descriptor for categorical data. It is based on polinomial distribution within the groups. 

## Fields

  * `size::Int`: The size of the dataset.
  * `groups::Vector{String}`: The names of the groups.
  * `rates::Vector{Float64}`: The probabilities of each group.
  * `cov_inv::Matrix{Float64}`: The inverse of the covariance matrix of the groups.
  * `group_active::Vector{Bool}`: A boolean vector indicating which groups are active (non-zero rates).

## Constructor

  * `CategoryMetric(size::Int, groups::Vector{String}, rates::Vector{Float64})`: Creates a new instance of CategoryMetric.  It validates the input data and calculates the inverse covariance matrix.
