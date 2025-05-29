```
exp(::MatricManifold{ℝ,<:SymmetricPositiveDefinite,<:GeneralizedBuresWassersteinMetric}, p, X)
```

[`SymmetricPositiveDefinite`](@ref) に関して [`GeneralizedBuresWassersteinMetric`](@ref) による指数写像を計算します。

$$
    \exp_p(X) = p+X+\mathcal ML_{p,M}(X)pML_{p,M}(X)
$$

ここで、$q=L_{M,p}(X)$ は一般化リーヤポフ演算子を示し、すなわち $pqM + Mqp = X$ を解きます。
