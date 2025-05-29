```
MeasurementGroup(measurements::Vector{MeasurementData{T}}) where {T <: Union{Nothing, AbstractMeasurementSetting}}
```

`MeasurementData` オブジェクトのベクトルから次元を推測して `MeasurementGroup` オブジェクトを構築します。

# 引数

  * `measurements::Vector{MeasurementData{T}}`: `MeasurementData` オブジェクトのベクトル。

# 戻り値

次の内容を持つ `MeasurementGroup` オブジェクト：

  * `N`: 最初の要素から推測される（すべての要素で一貫していると仮定）。
  * `NU`: 測定データオブジェクトの数。
  * `NM`: 最初の要素から推測される。
  * `measurements`: 提供されたベクトル。

# 例

```julia
setting1 = LocalUnitaryMeasurementSetting(4, ensemble="Haar")
results1 = rand(1:2, 10, 4)
data1 = MeasurementData(results1; measurement_setting=setting1)
setting2 = LocalUnitaryMeasurementSetting(4, ensemble="Haar")
results2 = rand(1:2, 10, 4)
data2 = MeasurementData(results2; measurement_setting=setting2)
group = MeasurementGroup([data1, data2])
```
