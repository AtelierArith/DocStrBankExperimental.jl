```
Random.rand(M::FixedRankMatrices; vector_at=nothing, kwargs...)
```

If `vector_at` is `nothing`, return a random point on the [`FixedRankMatrices`](@ref) manifold. The orthogonal matrices are sampled from the [`Stiefel`](@ref) manifold and the singular values are sampled uniformly at random.

If `vector_at` is not `nothing`, generate a random tangent vector in the tangent space of the point `vector_at` on the `FixedRankMatrices` manifold `M`.
