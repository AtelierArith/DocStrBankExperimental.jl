```
momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, species::AbstractParticleType, n::Val{N})
```

Returns the momentum of the `n`th particle in the given [`AbstractPhaseSpacePoint`](@ref) which has direction `dir` and species `species`. If `n` is outside the valid range for this phase space point, a `BoundsError` is thrown.

!!! note
    This function accepts n as a `Val{N}` type, i.e., a compile-time constant value (for example a literal `1` or `2`). This allows this function to add zero overhead, but **only** if `N` is actually known at compile time. If it is not, use the overload of this function that uses `n::Int` instead. That function is faster than calling this one with `Val(n)`.

