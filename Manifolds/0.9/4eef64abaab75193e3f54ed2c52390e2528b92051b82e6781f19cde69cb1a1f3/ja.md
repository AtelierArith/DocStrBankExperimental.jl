```
exp(::MatricManifold{ℝ,SymmetricPositiveDefinite,BuresWassersteinMetric}, p, X)
```

[`SymmetricPositiveDefinite`](@ref) に関して [`BuresWassersteinMetric`](@ref) による指数写像を計算します。

$$
    \exp_p(X) = p+X+L_p(X)pL_p(X)
$$

ここで $q=L_p(X)$ はリャプノフ演算子を示し、すなわち $pq + qp = X$ を解きます。
