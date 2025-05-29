```
reduce_to_subsystem(
group::MeasurementGroup{T},
subsystem::Vector{Int}
```

)::MeasurementGroup{T} where T <: LocalMeasurementSetting

指定されたサブシステムに`MeasurementGroup`オブジェクト（`LocalUnitaryMeasurementSetting`を持つ）を縮小します。

# 引数

  * `group::MeasurementGroup{LocalUnitaryMeasurementSetting}`: 元の測定データオブジェクト。
  * `subsystem::Vector{Int}`: 残すサブシステムを指定するサイトインデックスのベクトル（1ベース）。

# 戻り値

指定されたサブシステムに対応する新しい`MeasurementGroup`オブジェクト。
