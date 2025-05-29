```
inner(M::SymmetricPositiveDefinite, p, X, Y)
inner(M::MetricManifold{SymmetricPositiveDefinite,AffineInvariantMetric}, p, X, Y)
```

Compute the inner product of `X`, `Y` in the tangent space of `p` on the [`SymmetricPositiveDefinite`](@ref) manifold `M`, as a [`MetricManifold`](@ref) with [`AffineInvariantMetric`](@ref). The formula reads

$$
g_p(X,Y) = \operatorname{tr}(p^{-1} X p^{-1} Y),
$$
