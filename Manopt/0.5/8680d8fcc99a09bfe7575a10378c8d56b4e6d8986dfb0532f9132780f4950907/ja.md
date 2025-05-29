```
StopWhenPopulationCostConcentrated{TParam<:Real} <: StoppingCriterion
```

最後の `max_size` 世代における最良の目的関数値の範囲と現在の世代のすべての関数値が `tol` 未満である場合に停止します。これは [Hansen:2023](@cite) の `TolFun` 条件に対応します。

# コンストラクタ

```
StopWhenPopulationCostConcentrated(tol::Real, max_size::Int)
```
