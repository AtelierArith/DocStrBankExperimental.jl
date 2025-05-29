```
OneSampleTTest(xbar::Real, stddev::Real, n::Int, μ0::Real = 0)
```

平均 `xbar` と標本標準偏差 `stddev` を持つ `n` 値が平均 `μ0` の分布から来ているという帰無仮説に対して、分布が平均 `μ0` を持たないという対立仮説を検定するための一標本t検定を実行します。

実装: [`pvalue`](@ref), [`confint`](@ref)
