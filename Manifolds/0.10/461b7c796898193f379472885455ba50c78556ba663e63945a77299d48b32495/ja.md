```
inner(::MetricManifold{ℝ,SymmetricPositiveDefinite,BuresWassersteinMetric}, p, X, Y)
```

内積 [`SymmetricPositiveDefinite`](@ref) を [`BuresWassersteinMetric`](@ref) に関して次のように計算します。

$$
    ⟨X,Y⟩ = \frac{1}{2}\operatorname{tr}(L_p(X)Y)
$$

ここで、$q=L_p(X)$ はリャプノフ演算子を示し、すなわち $pq + qp = X$ を解きます。
