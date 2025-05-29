```julia
struct FuelCurve{T<:InfrastructureSystems.ValueCurve} <: InfrastructureSystems.ProductionVariableCostCurve{T<:InfrastructureSystems.ValueCurve}
```

  * `value_curve::InfrastructureSystems.ValueCurve`: この `ProductionVariableCostCurve` の基礎となる `ValueCurve` 表現
  * `power_units::InfrastructureSystems.UnitSystemModule.UnitSystem`: (デフォルト: 自然単位 (MW)) 曲線の x 軸の単位
  * `fuel_cost::Union{Float64, InfrastructureSystems.TimeSeriesKey}`: 固定の燃料コストの値または燃料コストの時系列への [`TimeSeriesKey`](@ref)
  * `vom_cost::InfrastructureSystems.LinearCurve`: (デフォルトは 0) :/(power_unit h) における追加の比例変動運用および保守コストを [`LinearCurve`](@ref) として表現

```
FuelCurve(value_curve, power_units, fuel_cost, vom_cost)
FuelCurve(value_curve, fuel_cost)
FuelCurve(value_curve, fuel_cost, vom_cost)
FuelCurve(value_curve, power_units, fuel_cost)
FuelCurve(; value_curve, power_units, fuel_cost, vom_cost)
```

燃料（MBTU、リットル、m^3 など）に関する発電所の変動運用コストの表現であり、燃料と通貨の間の換算係数が組み合わされています。入力-出力、増分、または平均レートデータを表す可能性のある [`ValueCurve`](@ref) で構成されています。x 軸のデフォルト単位は MW であり、`power_units` で指定できます。
