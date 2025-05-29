```julia
is_fermion(_::QEDbase.AbstractParticle) -> Bool

```

Interface function for particles. Return `true` if the passed subtype of [`AbstractParticle`](@ref) can be considered a *fermion* in the sense of particle statistics, and `false` otherwise. The default implementation of `is_fermion` for every subtype of [`AbstractParticle`](@ref) will always return `false`.
