```
AbstractParticleType <: AbstractParticle
```

This is the abstract base type for every species of particles. All functionalities defined on subtypes of `AbstractParticleType` should be static, i.e. known at compile time. For adding runtime information, e.g. four-momenta or particle states, to a particle, consider implementing a concrete subtype of [`AbstractParticle`](@ref) instead, which may have a type parameter `P<:AbstractParticleType`.

Concrete built-in subtypes of `AbstractParticleType` are available in `QEDcore.jl` and should always be singletons..
