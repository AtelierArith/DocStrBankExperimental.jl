```
mean(
    M::Hyperbolic,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = CyclicProximalPointEstimation();
    kwargs...,
)
```

Compute the Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) of `x` on the [`Hyperbolic`](@ref) space using [`CyclicProximalPointEstimation`](@extref `ManifoldsBase.CyclicProximalPointEstimation`).
