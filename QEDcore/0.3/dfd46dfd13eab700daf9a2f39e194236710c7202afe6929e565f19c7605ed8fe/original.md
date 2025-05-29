```
ParticleStateful <: AbstractParticle
```

Representation of a particle with a state. It has four fields:

  * `dir::ParticleDirection`: The direction of the particle, `Incoming()` or `Outgoing()`.
  * `species::AbstractParticleType`: The species of the particle, `Electron()`, `Positron()` etc.
  * `mom::AbstractFourMomentum`: The momentum of the particle.

Overloads for `is_fermion`, `is_boson`, `is_particle`, `is_anti_particle`, `is_incoming`, `is_outgoing`, `mass`, and `charge` are provided, delegating the call to the correct field and thus implementing the `AbstractParticle` interface.

```jldoctest
julia> using QEDcore

julia> ParticleStateful(Incoming(), Electron(), SFourMomentum(1, 0, 0, 0))
ParticleStateful: incoming electron
    momentum: [1.0, 0.0, 0.0, 0.0]

julia> ParticleStateful(Outgoing(), Photon(), SFourMomentum(1, 0, 0, 0))
ParticleStateful: outgoing photon
    momentum: [1.0, 0.0, 0.0, 0.0]
```
