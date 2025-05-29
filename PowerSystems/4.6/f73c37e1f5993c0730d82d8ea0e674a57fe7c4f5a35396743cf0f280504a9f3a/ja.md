```julia
mutable struct LoadCost <: PowerSystems.OperationalCost
```

  * `variable::InfrastructureSystems.CostCurve`: 変動費は[`CostCurve`](@ref)として表されます
  * `fixed::Float64`: (デフォルト: 0) 固定費。このフィールドは一部のコスト表現において重複する可能性があります

```
LoadCost(variable, fixed)
LoadCost(; variable, fixed)
```

制御可能な負荷（例: InterruptiblePowerLoad）のための運用コストで、固定費と変動費の要素を含みます。

`variable`コストは必須のパラメータですが、`zero(CostCurve)`を使用して0に設定することができます。
