```
mean(
    M::SymmetricPositiveDefinite,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = GeodesicInterpolation();
    kwargs...,
)
```

Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) を `x` に対して計算します [`GeodesicInterpolation`](@extref `ManifoldsBase.GeodesicInterpolation`) を使用して。
