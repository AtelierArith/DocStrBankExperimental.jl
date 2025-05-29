```
log(::MatricManifold{SymmetricPositiveDefinite,BuresWassersteinMetric}, p, q)
```

[`SymmetricPositiveDefinite`](@ref)に関して、[`BuresWassersteinMetric`](@ref)に基づく対数写像を計算します。

$$
    \log_p(q) = (pq)^{\frac{1}{2}} + (qp)^{\frac{1}{2}} - 2 p
$$

ここで、$q=L_p(X)$はリャプノフ演算子を示し、すなわち$pq + qp = X$を解きます。
