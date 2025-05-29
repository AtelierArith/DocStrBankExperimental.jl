```
OneSampleZTest(v::AbstractVector{T<:Real}, μ0::Real = 0)
```

ベクトル `v` のデータが平均 `μ0` を持つ分布から来ているという帰無仮説に対する一標本 z 検定を行い、分布が平均 `μ0` を持たないという対立仮説に対抗します。

実装: [`pvalue`](@ref), [`confint`](@ref)
