```
rand(::Unitary; vector_at=nothing, σ::Real=1.0)
```

Generate a random point on the [`UnitaryMatrices`](@ref) manifold, if `vector_at` is nothing, by computing the QR decomposition of a $n×x$ matrix.

Generate a tangent vector at `vector_at` by projecting a normally distributed matrix onto the tangent space.
