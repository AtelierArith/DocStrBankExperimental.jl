```julia
struct ParticleFilterTune{T<:ModelWrappers.Tagged, A<:BaytesCore.ParameterWeighting, B<:BaytesCore.ResamplingMethod, C<:BaytesFilters.ParticleReferencing, D, E, F, G, U<:BaytesCore.UpdateBool} <: BaytesCore.AbstractTune
```

Holds tuning information for Particle Filter.

# Fields

  * `tagged::ModelWrappers.Tagged`: Tagged Model parameter.
  * `weighting::BaytesCore.ParameterWeighting`: Weighting Methods for particles.
  * `resampling::BaytesCore.ResamplingMethod`: Resampling methods for particle trajectories.
  * `referencing::BaytesFilters.ParticleReferencing`: Referencing type for last particle at each iteration - either Conditional, Ancestral or Marginal Implementation.
  * `config::BaytesFilters.ParticleFilterConfig`: Contains data and reference size and sorting.
  * `chains::BaytesCore.ChainsTune`: Number of particle chains and tuning information.
  * `memory::BaytesFilters.ParticleFilterMemory`: Memory for latent and observed data.
  * `generated::BaytesCore.UpdateBool`: Boolean if generated quantities should be generated while sampling
  * `iter::BaytesCore.Iterator`: Current iteration.
