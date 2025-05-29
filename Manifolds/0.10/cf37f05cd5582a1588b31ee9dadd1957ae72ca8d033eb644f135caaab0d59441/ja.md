```
inner(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},<:StiefelSubmersionMetric}, p, X, Y)
```

[`Stiefel`](@ref)多様体上で[`StiefelSubmersionMetric`](@ref)に関する内積を計算します。式は次のようになります。

$$
g_p(X,Y) = \operatorname{tr}\bigl( X^{\mathrm{T}}(I_n - \frac{2α+1}{2(α+1)}pp^{\mathrm{T}})Y \bigr),
$$

ここで、$α$はメトリックのパラメータです。
