```
inner(M::SymmetricPositiveDefinite, p, X, Y)
inner(M::MetricManifold{SymmetricPositiveDefinite,AffineInvariantMetric}, p, X, Y)
```

点 `p` の接空間における `X` と `Y` の内積を、[`SymmetricPositiveDefinite`](@ref) 多様体 `M` 上で、[`MetricManifold`](@ref) として [`AffineInvariantMetric`](@ref) を用いて計算します。式は次のようになります。

$$
g_p(X,Y) = \operatorname{tr}(p^{-1} X p^{-1} Y),
$$
