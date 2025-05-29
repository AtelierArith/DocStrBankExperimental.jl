```julia
struct ParticleBuffer{A, I, P}
```

Contains temporary buffer values to avoid allocations during particle propagation.

# Fields

  * `parameter::BaytesCore.ParameterBuffer{A, I} where {A, I}`: Contains buffer values for particles and ancestor for one iteration.
  * `proposal::Vector`: Proposal trajectory and predicted latent variable.
  * `prediction::Vector`: Predicted latent and oberved data
  * `resampled::Vector{Bool}`: Stores boolean if resampled at each iteration.
  * `ℓobjectiveᵥ::Vector{Float64}`: Stores incremental log target estimates for each iteration.
