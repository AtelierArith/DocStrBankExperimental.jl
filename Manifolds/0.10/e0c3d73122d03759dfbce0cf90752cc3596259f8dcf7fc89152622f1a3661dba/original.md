```
mean(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::ExtrinsicEstimation;
    kwargs...,
)
```

Estimate the Riemannian center of mass of `x` using [`ExtrinsicEstimation`](@extref `ManifoldsBase.ExtrinsicEstimation`), i.e. by computing the mean in the embedding and projecting the result back.

See [`mean`](@ref mean(::AbstractManifold, ::AbstractVector, ::AbstractVector, ::GeodesicInterpolation)) for a description of the remaining `kwargs`.
