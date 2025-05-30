```
Weights(vs, wsum=sum(vs))
```

重み値 `vs` を持つ `Weights` ベクトルを構築します。事前に計算された合計を `wsum` として提供することができます。

`Weights` 型は、[`FrequencyWeights`](@ref)、[`AnalyticWeights`](@ref) および [`ProbabilityWeights`](@ref) に対して可能なすべての操作をサポートしない一般的な重みベクトルを説明します。
