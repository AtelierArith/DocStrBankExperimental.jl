```
StopWhenPopulationDiverges{TParam<:Real} <: StoppingCriterion
```

`σ` が最大偏差の `tol` を超えて増加した場合に停止します。これは通常、`σ` が非常に小さすぎるか、発散する挙動を示しています。これは [Hansen:2023](@cite) の `TolXUp` 条件に対応します。
