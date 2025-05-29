```
ExactOneSampleKSTest(x::AbstractVector{<:Real}, d::UnivariateDistribution)
```

ベクトル `x` のデータが分布 `d` から来ているという帰無仮説に対して、サンプルが `d` から抽出されていないという対立仮説のもとで、1サンプルの正確なコルモゴロフ–スミルノフ検定を実行します。

実装: [`pvalue`](@ref)
