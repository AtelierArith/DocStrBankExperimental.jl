```
DenseShadow(measurement_data::MeasurementData{LocalUnitaryMeasurementSetting}; G::Vector{Float64} = fill(1.0, size(measurement_data.N, 2)))
```

`MeasurementDataObject`から`DenseShadow`オブジェクトを構築します。

# 引数

  * `measurement_data::MeasurementData{LocalUnitaryMeasurementSetting}`:
  * `G::Vector{Float64}`（オプション）: 測定誤差を考慮するためのG値のベクトル（デフォルト: すべてのサイトに対して1.0）。

# 戻り値

`DenseShadow`オブジェクト。
