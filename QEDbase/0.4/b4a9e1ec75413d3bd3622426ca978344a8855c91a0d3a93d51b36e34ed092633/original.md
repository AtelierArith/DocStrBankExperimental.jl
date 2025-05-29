```julia
is_anti_particle(_::QEDbase.AbstractParticle) -> Bool

```

Interface function for particles. Return true if the passed subtype of [`AbstractParticle`](@ref) can be considered an *anti particle* as distinct from their particle counterpart, and `false` otherwise. The default implementation of `is_anti_particle` for every subtype of [`AbstractParticle`](@ref) will always return `false`.
