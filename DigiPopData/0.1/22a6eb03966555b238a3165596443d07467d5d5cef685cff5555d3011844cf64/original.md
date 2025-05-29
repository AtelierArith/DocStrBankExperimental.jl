"     SurvivalMetric <: AbstractMetric

## Fields

  * `size::Int`: The size of the dataset.
  * `levels::Vector{Float64}`: The survival levels (e.g. 0.9, 0.8, 0.7).
  * `values::Vector{Float64}`: The corresponding values for the survival levels.
  * `cov_inv::Matrix{Float64}`: The inverse of the covariance matrix of the groups.
  * `group_active::Vector{Bool}`: A boolean vector indicating which groups are active (non-zero rates).
  * `rates::Vector{Float64}`: The probabilities of each group.

## Constructor

  * `SurvivalMetric(size::Int, levels::Vector{Float64}, values::Vector{Float64})`: Creates a new instance of SurvivalMetric.  It validates the input data and calculates the inverse covariance matrix.
