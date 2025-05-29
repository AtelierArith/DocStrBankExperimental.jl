```
StopWhenSubgradientNormLess <: StoppingCriterion
```

現在のサブグラディエントノルムに基づく停止基準。

# コンストラクタ

```
StopWhenSubgradientNormLess(ε::Float64)
```

サブグラディエントの閾値 `ε` を持つ停止基準を作成します。つまり、この基準は [`get_subgradient`](@ref) がノルムが `ε` 未満のサブグラディエントベクトルを返すときに停止することを示します。
