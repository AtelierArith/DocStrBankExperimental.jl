```
BinomialTest(x::Integer, n::Integer, p::Real = 0.5)
BinomialTest(x::AbstractVector{Bool}, p::Real = 0.5)
```

`x` の成功が `n` 回の試行で得られたという帰無仮説に対して、成功確率 `p` が `p` に等しくないという対立仮説を検定するための二項検定を実行します（または、ベクトル `x` が得られた分布からのものと見なします）。

デフォルトで計算される信頼区間は Clopper-Pearson 区間です。信頼区間を計算するためのサポートされている方法のリストについては、[`confint(::BinomialTest)`](@ref) ドキュメントを参照してください。

実装: [`pvalue`](@ref), [`confint(::BinomialTest)`](@ref)
