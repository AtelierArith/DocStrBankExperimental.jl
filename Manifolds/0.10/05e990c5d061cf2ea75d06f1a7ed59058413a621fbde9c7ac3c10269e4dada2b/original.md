```
exp(M::SymmetricPositiveDefinite, p, X)
exp(M::MetricManifold{<:SymmetricPositiveDefinite,AffineInvariantMetric}, p, X)
```

Compute the exponential map from `p` with tangent vector `X` on the [`SymmetricPositiveDefinite`](@ref) `M` with its default [`MetricManifold`](@ref) having the [`AffineInvariantMetric`](@ref). The formula reads

$$
\exp_p X = p^{\frac{1}{2}}\operatorname{Exp}(p^{-\frac{1}{2}} X p^{-\frac{1}{2}})p^{\frac{1}{2}},
$$

where $\operatorname{Exp}$ denotes to the matrix exponential.
