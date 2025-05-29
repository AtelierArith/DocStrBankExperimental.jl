```
Particle{T}
```

# Fields

  * `Θ::Vector{T}`: a vector of parameters
  * `accept::Vector{Bool}`: proposal acceptance. 1: accept, 0: reject
  * `weight::Float64`: particle weight based on model fit (currently posterior log likelihood)
  * `lp::Vector{Float64}`: a vector of log posterior probabilities associated with each accepted proposal
  * `id::Int`: particle id
