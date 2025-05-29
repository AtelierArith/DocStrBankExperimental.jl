```julia
mutable struct StorageCost <: PowerSystems.OperationalCost
```

  * `charge_variable_cost::InfrastructureSystems.CostCurve`: (デフォルトは0) [`CostCurve`](@ref)として表される充電の変動コスト
  * `discharge_variable_cost::InfrastructureSystems.CostCurve`: (デフォルトは0) [`CostCurve`](@ref)として表される放電の変動コスト
  * `fixed::Float64`: (デフォルト: 0) ストレージシステムの運用にかかる固定コスト
  * `start_up::Union{Float64, @NamedTuple{charge::Float64, discharge::Float64}}`: (デフォルト: 0) 起動コスト
  * `shut_down::Float64`: (デフォルト: 0) 停止コスト
  * `energy_shortage_cost::Float64`: (デフォルト: 0) エネルギー目標が不足した場合にモデルが負担するコスト
  * `energy_surplus_cost::Float64`: (デフォルト: 0) 余剰エネルギーが蓄えられた場合にモデルが負担するコスト

```
StorageCost(charge_variable_cost, discharge_variable_cost, fixed, start_up, shut_down, energy_shortage_cost, energy_surplus_cost)
StorageCost(; charge_variable_cost, discharge_variable_cost, fixed, start_up, shut_down, energy_shortage_cost, energy_surplus_cost)
```

ストレージユニットの運用コストで、固定コストと充電または放電の変動コストを含みます。

このデータ構造は、買い/売りの入札の提出などの市場ストレージシステムの市場運用を表すことを意図していません – 代わりに[`MarketBidCost`](@ref)を参照してください。
