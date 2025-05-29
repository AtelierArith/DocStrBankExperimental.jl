```
reduce_to_subsystem(settings, subsystem)
```

`LocalMeasurementSetting`オブジェクトを指定されたサブシステムに縮小します。

# 引数:

  * `settings::LocalMeasurementSetting`: 元の測定設定オブジェクト。
  * `subsystem::Vector{Int}`: 残すサブシステムを指定するサイトインデックスのベクトル（1ベース）。

# 戻り値:

  * 指定されたサブシステムに対応する新しい`LocalMeasurementSetting`オブジェクト。

# 例:

```julia
reduced_setting = reduce_to_subsystem(full_setting, [1, 3])
```
