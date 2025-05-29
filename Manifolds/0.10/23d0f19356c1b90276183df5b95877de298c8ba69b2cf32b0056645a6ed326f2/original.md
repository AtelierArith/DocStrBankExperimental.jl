```
inner(N::MetricManifold{M,G}, p, X, Y)
```

Compute the inner product of `X` and `Y` from the tangent space at `p` on the [`AbstractManifold`](https://juliamanifolds.github.io/Manifolds.jl/latest/interface.html#ManifoldsBase.AbstractManifold) `M` using the [`AbstractMetric`](@extref `ManifoldsBase.AbstractMetric`) `G`. If `M` has `G` as its [`IsDefaultMetric`](@ref) trait, this is done using `inner(M, p, X, Y)`, otherwise the [`local_metric`](@ref)`(M, p)` is employed as

$$
g_p(X, Y) = ⟨X, G_p Y⟩,
$$

where $G_p$ is the loal matrix representation of the `AbstractMetric` `G`.
