```
inner(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},<:StiefelSubmersionMetric}, p, X, Y)
```

Compute the inner product on the [`Stiefel`](@ref) manifold with respect to the [`StiefelSubmersionMetric`](@ref). The formula reads

$$
g_p(X,Y) = \operatorname{tr}\bigl( X^{\mathrm{T}}(I_n - \frac{2α+1}{2(α+1)}pp^{\mathrm{T}})Y \bigr),
$$

where $α$ is the parameter of the metric.
