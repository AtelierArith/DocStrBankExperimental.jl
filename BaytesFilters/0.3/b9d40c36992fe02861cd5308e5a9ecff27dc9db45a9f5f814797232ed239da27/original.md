```julia
struct ParticleFilterDefault{M<:Union{Nothing, BaytesFilters.ParticleFilterMemory}, A<:BaytesCore.ParameterWeighting, B<:BaytesCore.ResamplingMethod, C<:BaytesFilters.ParticleReferencing, T<:Integer, I<:ModelWrappers.AbstractInitialization, U<:BaytesCore.UpdateBool}
```

Default arguments for Particle Filter constructor.

# Fields

  * `memory::Union{Nothing, BaytesFilters.ParticleFilterMemory}`: Memory for particles and data.
  * `weighting::BaytesCore.ParameterWeighting`: Weighting Methods for particles.
  * `resampling::BaytesCore.ResamplingMethod`: Resampling methods for particle trajectories.
  * `referencing::BaytesFilters.ParticleReferencing`: Referencing type for last particle at each iteration - either Conditional, Ancestral or Marginal Implementation.
  * `coverage::Float64`: Coverage of Particles/datapoints.
  * `threshold::Float64`: ESS threshold for resampling particle trajectories.
  * `ancestortype::Type{T} where T<:Integer`: Type for ancestors indices
  * `init::ModelWrappers.AbstractInitialization`: Method to obtain initial Modelparameter, see 'AbstractInitialization'.
  * `generated::BaytesCore.UpdateBool`: Boolean if generate(_rng, objective) for corresponding model is stored in PF Diagnostics.
