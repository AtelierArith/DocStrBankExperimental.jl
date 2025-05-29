```julia
mutable struct RenewableGenerationCost <: PowerSystems.OperationalCost
```

  * `variable::InfrastructureSystems.CostCurve`: 変動費用は[`CostCurve`](@ref)として表されます
  * `curtailment_cost::InfrastructureSystems.CostCurve`: (デフォルトは0) 電力の抑制にかかる費用は[`CostCurve`](@ref)として表されます

```
RenewableGenerationCost(variable, curtailment_cost)
RenewableGenerationCost(variable; curtailment_cost)
RenewableGenerationCost(; variable, curtailment_cost)
```

再生可能発電機の運用コストで、エネルギーの変動費用（例えば、[PPA](@ref P)のような）と電力の抑制にかかる費用を含みます。例えば、抑制コストは税制優遇の損失を表すために使用されることがあります。

`variable`コストは必須のパラメータですが、`zero(CostCurve)`を使用して0に設定することができます。
