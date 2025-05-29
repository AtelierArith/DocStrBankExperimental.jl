```julia
is_particle(_::QEDbase.AbstractParticle) -> Bool

```

Interface function for particles. Return `true` if the passed subtype of [`AbstractParticle`](@ref) can be considered a *particle* as distinct from anti-particles, and `false` otherwise. The default implementation of `is_particle` for every subtype of [`AbstractParticle`](@ref) will always return `true`.
