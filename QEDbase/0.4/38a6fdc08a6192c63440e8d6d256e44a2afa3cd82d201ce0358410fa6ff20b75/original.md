```
momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, n::Int)
```

Returns the momentum of the `n`th particle in the given [`AbstractPhaseSpacePoint`](@ref) which has direction `dir`. If `n` is outside the valid range for this phase space point, a `BoundsError` is thrown.
