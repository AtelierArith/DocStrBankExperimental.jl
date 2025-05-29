```
mean(
    M::Hyperbolic,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = CyclicProximalPointEstimation();
    kwargs...,
)
```

Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) を使用して、[`Hyperbolic`](@ref) 空間上の `x` の平均を [`CyclicProximalPointEstimation`](@extref `ManifoldsBase.CyclicProximalPointEstimation`) で計算します。
