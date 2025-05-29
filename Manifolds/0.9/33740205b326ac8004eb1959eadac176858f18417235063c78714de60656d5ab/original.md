```
rand(::MultinomialDoubleStochastic; vector_at=nothing, σ::Real=1.0, kwargs...)
```

Generate random points on the [`MultinomialDoubleStochastic`](@ref) manifold or tangent vectors at the point `vector_at` if that is not `nothing`.

Let $n×n$ denote the matrix dimension of the [`MultinomialDoubleStochastic`](@ref).

When `vector_at` is nothing, this is done by generating a random matrix`rand(n,n)` with positive entries and projecting it onto the manifold. The `kwargs...` are passed to this projection.

When `vector_at` is not `nothing`, a random matrix in the ambient space is generated and projected onto the tangent space
