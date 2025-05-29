```
OneSampleTTest(v::AbstractVector{T<:Real}, μ0::Real = 0)
```

ベクトル `v` のデータが平均 `μ0` を持つ分布から来ているという帰無仮説に対して、分布が平均 `μ0` を持たないという対立仮説の一標本t検定を実行します。

実装: [`pvalue`](@ref), [`confint`](@ref)
