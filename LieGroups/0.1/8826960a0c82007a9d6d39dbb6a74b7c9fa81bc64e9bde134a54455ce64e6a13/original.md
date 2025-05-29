```
rand(::LieGroup; vector_at=nothing, σ=1.0, kwargs...)
rand(::LieAlgebra; σ=1.0, kwargs...)
rand!(::AbstractLieGroup, gX; vector_at=nothing, kwargs...)
rand!(::LieAlgebra, X; σ=1.0, kwargs...)
```

Compute a random point or tangent vector on a Lie group.

For points this just means to generate a random point on the underlying manifold itself.

For tangent vectors, an element in the Lie Algebra is generated, see also [`rand(::LieAlgebra; kwargs...)`](@ref)
