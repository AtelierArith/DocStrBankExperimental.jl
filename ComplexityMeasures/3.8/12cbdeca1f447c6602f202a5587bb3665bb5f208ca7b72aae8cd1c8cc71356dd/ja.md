```
information_maximum(e::InformationMeasure, o::OutcomeSpace [, x])
```

与えられた情報量測定の最大値を返します。入力データ `x` と与えられた結果空間に基づいています（[`OutcomeSpace`](@ref) は [`ProbabilitiesEstimator`](@ref) によって指定することもできます）。

[`outcome_space`](@ref) のように、いくつかの結果空間では、可能な結果が入力 `x` の知識なしに知られている場合があり、その場合、関数は `information_maximum(e, o)` にディスパッチされます。

```
information_maximum(e::InformationMeasure, L::Int)
```

上記と同じですが、全結果の数 `L` から直接計算されます。
