```
exp(M::SymmetricPositiveDefinite, p, X)
exp(M::MetricManifold{<:SymmetricPositiveDefinite,AffineInvariantMetric}, p, X)
```

点 `p` から接ベクトル `X` に沿った指数写像を [`SymmetricPositiveDefinite`](@ref) `M` で計算し、そのデフォルトの [`MetricManifold`](@ref) は [`AffineInvariantMetric`](@ref) を持ちます。式は次のようになります。

$$
\exp_p X = p^{\frac{1}{2}}\operatorname{Exp}(p^{-\frac{1}{2}} X p^{-\frac{1}{2}})p^{\frac{1}{2}},
$$

ここで、$\operatorname{Exp}$ は行列の指数を示します。
