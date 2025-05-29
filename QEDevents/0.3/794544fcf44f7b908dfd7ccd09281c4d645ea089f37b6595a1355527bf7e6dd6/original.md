MultiParticleDistribution

Base type for sample drawing from multiple particle distributions. The following interface functions should be implemented:

  * [`QEDevents._particles(d::MultiParticleDistribution)`](@ref)
  * [`QEDevents._particle_directions(d::MultiParticleDistribution)`](@ref)
  * [`QEDevents._randmom(rng::AbstractRNG,d::MultiParticleDistribution)`](@ref)
