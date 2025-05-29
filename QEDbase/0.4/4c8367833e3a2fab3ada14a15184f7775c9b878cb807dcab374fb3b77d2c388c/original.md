```
momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, species::AbstractParticleType)
```

Returns the momentum of the particle in the given [`AbstractPhaseSpacePoint`](@ref) with `dir` and `species`, *if* there is only one such particle. If there are multiple or none, an [`InvalidInputError`](@ref) is thrown.
