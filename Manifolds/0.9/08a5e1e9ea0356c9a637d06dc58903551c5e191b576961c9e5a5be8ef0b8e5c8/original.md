```
q = exp(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},<:StiefelSubmersionMetric}, p, X)
exp!(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},<:StiefelSubmersionMetric}, q, p, X)
```

Compute the exponential map on the [`Stiefel(n,k)`](@ref) manifold with respect to the [`StiefelSubmersionMetric`](@ref).

The exponential map is given by

$$
\exp_p X = \operatorname{Exp}\bigl(
    -\frac{2α+1}{α+1} p p^\mathrm{T} X p^\mathrm{T} +
    X p^\mathrm{T} - p X^\mathrm{T}
\bigr) p \operatorname{Exp}\bigl(\frac{\alpha}{\alpha+1} p^\mathrm{T} X\bigr)
$$

This implementation is based on [ZimmermannHueper:2022](@cite).

For $k < \frac{n}{2}$ the exponential is computed more efficiently using [`StiefelFactorization`](@ref).
