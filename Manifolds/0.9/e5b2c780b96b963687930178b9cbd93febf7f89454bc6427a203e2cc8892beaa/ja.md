```
exp(M::MetricManifold{SymmetricPositiveDefinite,LogCholeskyMetric}, p, X)
```

[`SymmetricPositiveDefinite`](@ref) `M`上で[`LogCholeskyMetric`](@ref)を用いて、点`p`から方向`X`への指数写像を計算します。式は次のようになります。

$$
\exp_p X = (\exp_y W)(\exp_y W)^\mathrm{T}
$$

ここで、$\exp_xW$は[`CholeskySpace`](@ref)上の指数写像であり、$y$は$p$のコレスキー分解、$W = y(y^{-1}Xy^{-\mathrm{T}})_\frac{1}{2}$、および$(⋅)_\frac{1}{2}$は対角成分が$\frac{1}{2}$倍された下三角行列を示します。
