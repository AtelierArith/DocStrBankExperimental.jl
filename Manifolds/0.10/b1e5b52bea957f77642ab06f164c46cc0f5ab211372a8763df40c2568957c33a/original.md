```
local_metric(M::AbstractManifold{𝔽}, p, B::AbstractBasis)
```

Return the local matrix representation at the point `p` of the metric tensor $g$ with respect to the [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) `B` on the [`AbstractManifold`](https://juliamanifolds.github.io/Manifolds.jl/latest/interface.html#ManifoldsBase.AbstractManifold) `M`. Let $d$denote the dimension of the manifold and $b_1,\ldots,b_d$ the basis vectors. Then the local matrix representation is a matrix $G\in 𝔽^{n×n}$ whose entries are given by $g_{ij} = g_p(b_i,b_j), i,j\in\{1,…,d\}$.

This yields the property for two tangent vectors (using Einstein summation convention) $X = X^ib_i, Y=Y^ib_i \in T_p\mathcal M$ we get $g_p(X, Y) = g_{ij} X^i Y^j$.
