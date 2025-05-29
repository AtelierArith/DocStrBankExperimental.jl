```
log(M::SymmetricPositiveDefinite, p, q)
log(M::MetricManifold{SymmetricPositiveDefinite,AffineInvariantMetric}, p, q)
```

点 `p` から点 `q` への [`SymmetricPositiveDefinite`](@ref) 上の [`MetricManifold`](@ref) としての [`AffineInvariantMetric`](@ref) からの対数写像を計算します。式は次のようになります。

$$
\log_p q =
p^{\frac{1}{2}}\operatorname{Log}(p^{-\frac{1}{2}}qp^{-\frac{1}{2}})p^{\frac{1}{2}},
$$

ここで、$\operatorname{Log}$ は行列の対数を示します。
