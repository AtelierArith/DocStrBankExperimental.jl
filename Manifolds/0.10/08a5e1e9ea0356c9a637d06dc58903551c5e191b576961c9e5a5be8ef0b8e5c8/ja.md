```
q = exp(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},<:StiefelSubmersionMetric}, p, X)
exp!(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},<:StiefelSubmersionMetric}, q, p, X)
```

[`Stiefel(n,k)`](@ref) 多様体における [`StiefelSubmersionMetric`](@ref) に関する指数写像を計算します。

指数写像は次のように与えられます。

$$
\exp_p X = \operatorname{Exp}\bigl(
    -\frac{2α+1}{α+1} p p^\mathrm{T} X p^\mathrm{T} +
    X p^\mathrm{T} - p X^\mathrm{T}
\bigr) p \operatorname{Exp}\bigl(\frac{\alpha}{\alpha+1} p^\mathrm{T} X\bigr)
$$

この実装は [ZimmermannHueper:2022](@cite) に基づいています。

$$
k < \frac{n}{2}
$$

の場合、指数は [`StiefelFactorization`](@ref) を使用してより効率的に計算されます。
