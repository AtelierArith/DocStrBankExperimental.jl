```
log(N::MetricManifold{M,G}, p, q)
```

Compute the logarithmic map on the [`AbstractManifold`](https://juliamanifolds.github.io/Manifolds.jl/latest/interface.html#ManifoldsBase.AbstractManifold) `M` equipped with the [`AbstractMetric`](@extref `ManifoldsBase.AbstractMetric`) `G`.

If the metric was declared the default metric using the [`IsDefaultMetric`](@ref) trait or [`is_default_metric`](@ref), this method falls back to `log(M,p,q)`. Otherwise, you have to provide an implementation for the non-default `AbstractMetric` `G` metric within its [`MetricManifold`](@ref)`{M,G}`.
