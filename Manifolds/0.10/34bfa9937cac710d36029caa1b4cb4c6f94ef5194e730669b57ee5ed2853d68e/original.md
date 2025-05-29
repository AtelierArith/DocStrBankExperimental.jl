```
median(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::ExtrinsicEstimation;
    kwargs...,
)
```

Estimate the median of `x` using [`ExtrinsicEstimation`](@extref `ManifoldsBase.ExtrinsicEstimation`), i.e. by computing the median in the embedding and projecting the result back.

See [`median`](@ref median(::AbstractManifold, ::AbstractVector, ::AbstractVector, ::CyclicProximalPointEstimation)) for a description of `kwargs`.
