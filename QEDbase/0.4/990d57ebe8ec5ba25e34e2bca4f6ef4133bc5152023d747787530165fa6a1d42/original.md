```julia
is_boson(_::QEDbase.AbstractParticle) -> Bool

```

Interface function for particles. Return `true` if the passed subtype of [`AbstractParticle`](@ref) can be considered a *boson* in the sense of particle statistics, and `false` otherwise. The default implementation of `is_boson` for every subtype of [`AbstractParticle`](@ref) will always return `false`.
