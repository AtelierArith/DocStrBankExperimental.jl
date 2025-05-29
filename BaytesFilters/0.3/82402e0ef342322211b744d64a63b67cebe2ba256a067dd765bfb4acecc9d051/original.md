```julia
struct ParticleFilter{A<:BaytesFilters.Particles, B<:BaytesFilters.ParticleFilterTune} <: BaytesCore.AbstractAlgorithm
```

Contains particles, transition kernel and all other relevant tuning information for particle propagation.

# Fields

  * `particles::BaytesFilters.Particles`: Particle values and kernel.
  * `tune::BaytesFilters.ParticleFilterTune`: Tuning configuration for particles.
