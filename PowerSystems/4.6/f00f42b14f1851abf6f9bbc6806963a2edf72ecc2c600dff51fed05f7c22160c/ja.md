```julia
mutable struct ThermalGenerationCost <: PowerSystems.OperationalCost
```

  * `variable::InfrastructureSystems.ProductionVariableCostCurve`: 変動生産コスト。[`CostCurve`](@ref) または [`FuelCurve`](@ref) を取ることができます。
  * `fixed::Float64`: ユニットをオンラインに保つための固定コスト。一部のコスト表現では、このフィールドは重複する可能性があります。
  * `start_up::Union{Float64, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}}`: 起動コストは線形または多段階コストを取ることができます。
  * `shut_down::Float64`: ユニットをオフにするためのコスト

```
ThermalGenerationCost(variable, fixed, start_up, shut_down)
ThermalGenerationCost(; variable, fixed, start_up, shut_down)
```

熱発電機の運用コストで、固定コスト、変動コスト、シャットダウンコスト、そして複数の起動コストのオプションを含みます。
