```
inner(::MetricManifold{ℝ,<:SymmetricPositiveDefinite,<:GeneralizedBuresWassersteinMetric}, p, X, Y)
```

内積 [`SymmetricPositiveDefinite`](@ref) を [`GeneralizedBuresWassersteinMetric`](@ref) に関して次のように計算します。

$$
    ⟨X,Y⟩ = \frac{1}{2}\operatorname{tr}(L_{p,M}(X)Y)
$$

ここで、$q=L_{M,p}(X)$ は一般化リャプノフ演算子を示し、すなわち $pqM + Mqp = X$ を解きます。
