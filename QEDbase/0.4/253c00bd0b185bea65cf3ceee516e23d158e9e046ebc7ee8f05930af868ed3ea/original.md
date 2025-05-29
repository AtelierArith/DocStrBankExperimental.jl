```
AbstractParticleStateful <: QEDbase.AbstractParticle
```

Abstract base type for the representation of a particle with a state. It requires the following interface functions to be provided:

  * [`particle_direction`](@ref): Returning the particle's direction.
  * [`particle_species`](@ref): Returning the particle's species.
  * [`momentum`](@ref): Returning the particle's momentum.

Implementations for [`is_fermion`](@ref), [`is_boson`](@ref), [`is_particle`](@ref), [`is_anti_particle`](@ref), [`is_incoming`](@ref), [`is_outgoing`](@ref), [`mass`](@ref), and [`charge`](@ref) are automatically provided using the interface functions above to fulfill the [`QEDbase.AbstractParticle`](@ref) interface.
