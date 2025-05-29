```
MeasurementData(measurement_results::Array{Int, 2}; measurement_setting::Union{T, Nothing} = nothing)
```

`MeasurementData`オブジェクトを作成し、測定結果の次元を推測し、提供された設定を検証します。

# 引数

  * `measurement_results::Array{Int, 2}`: 形状が `(NM, N)` の2Dバイナリ測定結果の配列。
  * `measurement_setting::Union{T <: AbstractMeasurementSetting, Nothing}` (オプション): 測定設定または提供されていない場合は `nothing`。

# 戻り値

推測された次元と検証された設定を持つ `MeasurementData` オブジェクト。

# 例外

  * `AssertionError`: `measurement_results` と `measurement_setting` の次元が不一致の場合。

# 例

```julia
# 測定設定あり
setting = LocalUnitaryMeasurementSetting(4, ensemble="Haar")
results = rand(1:2, 10, 4)
data_with_setting = MeasurementData(results; measurement_setting=setting)

# 測定設定なし
data_without_setting = MeasurementData(rand(1:2, 10, 4))
```
