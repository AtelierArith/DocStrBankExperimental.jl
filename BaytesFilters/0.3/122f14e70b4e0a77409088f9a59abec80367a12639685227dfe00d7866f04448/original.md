```julia
mutable struct Particles{R, B, I<:Integer} <: BaytesFilters.AbstractParticles
```

Contains Particle container for propagation.

# Fields

  * `val::ElasticArrays.ElasticArray{B, 2, 1, Vector{B}} where B`: Particle trajectories, for a discussion about possible shapes for the trajectories.
  * `ancestor::ElasticArrays.ElasticArray{I, 2, 1, Vector{I}} where I<:Integer`: Saved ancestors of resampling step in pf
  * `weights::BaytesCore.ParameterWeights`: Particle weights.
  * `buffer::BaytesFilters.ParticleBuffer{B, I, R} where {R, B, I<:Integer}`: Necessary buffer values for resampling particles.
  * `ℓobjective::BaytesCore.Accumulator`: Log likelihood estimate.
