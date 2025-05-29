```
inner(M::MetricManifold{ℝ, Stiefel{<:Any,ℝ}, X, CanonicalMetric}, p, X, Y)
```

Compute the inner product on the [`Stiefel`](@ref) manifold with respect to the [`CanonicalMetric`](@ref). The formula reads

$$
g_p(X,Y) = \operatorname{tr}\bigl( X^{\mathrm{T}}(I_n - \frac{1}{2}pp^{\mathrm{T}})Y \bigr).
$$
