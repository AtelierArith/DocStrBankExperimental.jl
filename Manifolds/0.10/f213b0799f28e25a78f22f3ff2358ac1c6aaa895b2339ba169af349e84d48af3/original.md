```
rand(::GeneralizedStiefel; vector_at=nothing, σ::Real=1.0)
```

When `vector_at` is `nothing`, return a random (Gaussian) point `p` on the [`GeneralizedStiefel`](@ref) manifold `M` by generating a (Gaussian) matrix with standard deviation `σ` and return the (generalized) orthogonalized version, i.e. return the projection onto the manifold of the Q component of the QR decomposition of the random matrix of size $n×k$.

When `vector_at` is not `nothing`, return a (Gaussian) random vector from the tangent space $T_{vector\_at}\mathrm{St}(n,k)$ with mean zero and standard deviation `σ` by projecting a random Matrix onto the tangent vector at `vector_at`.
