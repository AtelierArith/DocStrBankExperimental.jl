```
median(M::AbstractManifold, x::AbstractVector[, w::AbstractWeights]; kwargs...)
median(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::AbstractApproximationMethod;
    kwargs...,
)
```

Compute the (optionally weighted) Riemannian median of the vector `x` of points on the [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)  `M`, defined as the point that satisfies the minimizer

$$
\operatorname{argmin}_{y ∈ \mathcal M} \frac{1}{\sum_{i=1}^n w_i} \sum_{i=1}^n w_i\mathrm{d}_{\mathcal M}(y,x_i),
$$

where $\mathrm{d}_{\mathcal M}$ denotes the Riemannian [`distance`](@ref). This function is nonsmooth (i.e nondifferentiable).

In the general case, the [`CyclicProximalPointEstimation`](@extref `ManifoldsBase.CyclicProximalPointEstimation`) is used to compute the median. However, this default may be overloaded for specific manifolds.

Compute the median using the specified `method`.
