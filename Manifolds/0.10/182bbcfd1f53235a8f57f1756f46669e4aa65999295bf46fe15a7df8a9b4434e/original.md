```
inverse_local_metric(M::AbstractcManifold{𝔽}, p, B::AbstractBasis)
```

Return the local matrix representation of the inverse metric (cometric) tensor of the tangent space at `p` on the [`AbstractManifold`](https://juliamanifolds.github.io/Manifolds.jl/latest/interface.html#ManifoldsBase.AbstractManifold) `M` with respect to the [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) basis `B`.

The metric tensor (see [`local_metric`](@ref)) is usually denoted by $G = (g_{ij}) ∈ 𝔽^{d×d}$, where $d$ is the dimension of the manifold.

Then the inverse local metric is denoted by $G^{-1} = g^{ij}$.
