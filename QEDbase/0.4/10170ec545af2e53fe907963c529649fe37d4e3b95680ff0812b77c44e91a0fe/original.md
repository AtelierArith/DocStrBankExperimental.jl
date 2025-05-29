```
momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, species::AbstractParticleType, n::Int)
```

Returns the momentum of the `n`th particle in the given [`AbstractPhaseSpacePoint`](@ref) which has direction `dir` and species `species`. If `n` is outside the valid range for this phase space point, a `BoundsError` is thrown.

!!! note
    This function accepts n as an `Int` value. If `n` is a compile-time constant (for example, a literal `1` or `2`), you can use `Val(n)` instead to call a zero overhead version of this function.

