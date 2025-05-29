```julia
struct ParameterWeights
```

Container for weights and normalized particles weights at current time step t.

# Fields

  * `ℓweights::Vector{Float64}`: Used for log likelihood calculation.
  * `ℓweightsₙ::Vector{Float64}`: exp(ℓweightsₙ) used for resampling particles and sampling trajectories ~ kept in log space for numerical stability.
  * `buffer::Vector{Float64}`: A buffer vector with same size as ℓweights and ℓweightsₙ.
