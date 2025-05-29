```
mean(
    M::ProbabilitySimplex,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = GeodesicInterpolation();
    kwargs...,
)
```

Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) を使用して `x` の計算を行います [`GeodesicInterpolation`](@extref `ManifoldsBase.GeodesicInterpolation`)。
