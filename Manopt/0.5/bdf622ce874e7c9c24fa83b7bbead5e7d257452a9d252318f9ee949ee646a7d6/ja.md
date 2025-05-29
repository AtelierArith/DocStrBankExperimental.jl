```
StopWhenBestCostInGenerationConstant <: StoppingCriterion
```

最後の `iteration_range` 世代の最良目的関数値の範囲がゼロの場合に停止します。これは [Hansen:2023](@cite) の `EqualFUnValues` 条件に対応します。

また、`StopWhenPopulationCostConcentrated` も参照してください。
