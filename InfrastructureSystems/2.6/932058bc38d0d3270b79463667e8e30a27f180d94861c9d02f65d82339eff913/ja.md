```julia
struct CostCurve{T<:InfrastructureSystems.ValueCurve} <: InfrastructureSystems.ProductionVariableCostCurve{T<:InfrastructureSystems.ValueCurve}
```

  * `value_curve::InfrastructureSystems.ValueCurve`: この `ProductionVariableCostCurve` の基礎となる `ValueCurve` 表現
  * `power_units::InfrastructureSystems.UnitSystemModule.UnitSystem`: (デフォルト: 自然単位 (MW)) 曲線の x 軸の単位
  * `vom_cost::InfrastructureSystems.LinearCurve`: (デフォルトは 0) 追加の比例変動運用および保守コスト :/(power_unit h) として表され、[`LinearCurve`](@ref) として表現される

```
CostCurve(value_curve, power_units, vom_cost)
CostCurve(; value_curve, power_units, vom_cost)
```

通貨での発電所の変動運用コストの直接的な表現。入力-出力、増分、または平均レートデータを表す可能性のある [`ValueCurve`](@ref) で構成されています。x 軸のデフォルト単位は MW であり、`power_units` で指定できます。
