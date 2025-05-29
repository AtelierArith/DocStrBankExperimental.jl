```
rand(::AbstractLieGroup; vector_at=nothing, σ::Real=1.0, kwargs...)
rand(::AbstractLieGroup, PT::Type; vector_at=nothing, σ::Real=1.0, kwargs...)
rand!(::LieAlgebra, T::Type; σ::Real=1.0, kwargs...)
rand!(::AbstractLieGroup, gX::PT; vector_at=nothing, σ::Real=1.0, kwargs...)
rand!(::LieAlgebra, X::T; σ::Real=1.0, kwargs...)
```

Compute a random point or tangent vector on a Lie group.

For points this just means to generate a random point on the underlying manifold itself.

For tangent vectors, an element in the Lie Algebra is generated, see also [`rand(::LieAlgebra; kwargs...)`](@ref)

For both cases, you can provide the type $T$ for the tangent vector and/or point $PT$, if you want to generate a random point in a certain representation. For the in-place variants the type is inferred from `pX´ and`X`, respectively.
