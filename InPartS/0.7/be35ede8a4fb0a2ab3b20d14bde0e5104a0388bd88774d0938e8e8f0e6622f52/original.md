```
AbstractRegistrar{T}
```

Abstract type for registrars. Subtypes `XxxxRegistrar{T}` should implement a function

```julia
get_id!(reg::XxxxRegistrar{T}, parent::T, sim::Simulation, futureparticle::AbstractParticle) → T
```

that returns (preferably unique) identifers of type `T` on every call. Comes with a helper function [`_idtype`](@ref) that returns `T`.
