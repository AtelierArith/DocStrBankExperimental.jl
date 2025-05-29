```julia
mutable struct HydroGenerationCost <: PowerSystems.OperationalCost
```

  * `variable::InfrastructureSystems.ProductionVariableCostCurve`: 生産変動コストは `FuelCurve` で表され、水が燃料であるか、通貨での `CostCurve` です。
  * `fixed::Float64`: (デフォルト: 0) ユニットをオンラインに保つための固定コスト。このフィールドは、いくつかのコスト表現において重複する可能性があります。

```
HydroGenerationCost(variable, fixed)
HydroGenerationCost(; variable, fixed)
```

固定コストと変動コストを含む水力発電機の運用コスト。変動コストは、負の値を使用することでカーテイメントのコストを表現したり、正のコストの場合は水の機会コストを表現するために使用できます。また、特定の水の取り入れをモデル化するために燃料曲線もサポートしています。

`variable` コストは必須のパラメータですが、`zero(CostCurve)` を使用して 0 に設定することができます。
