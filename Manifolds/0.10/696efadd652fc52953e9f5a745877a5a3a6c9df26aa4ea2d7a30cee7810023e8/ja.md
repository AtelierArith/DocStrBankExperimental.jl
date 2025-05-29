```
inner(M::MetricManifold{ℝ, Stiefel{<:Any,ℝ}, X, CanonicalMetric}, p, X, Y)
```

[`CanonicalMetric`](@ref)に関して[`Stiefel`](@ref)多様体上の内積を計算します。式は次のようになります。

$$
g_p(X,Y) = \operatorname{tr}\bigl( X^{\mathrm{T}}(I_n - \frac{1}{2}pp^{\mathrm{T}})Y \bigr).
$$
