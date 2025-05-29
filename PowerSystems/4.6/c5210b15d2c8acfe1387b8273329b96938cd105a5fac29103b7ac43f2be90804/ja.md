```julia
add_time_series!(
    sys::PowerSystems.System,
    file_metadata::Vector{InfrastructureSystems.TimeSeriesFileMetadata};
    resolution
) -> Vector{InfrastructureSystems.TimeSeriesKey}

```

メタデータファイルまたはメタデータ記述子から時系列データを追加します。

# 引数

  * `sys::System`: システム
  * `timeseries_metadata::Vector{IS.TimeSeriesFileMetadata}`: 時系列のメタデータ
  * `resolution::DateTime.Period=nothing`: この解像度に一致しない時系列をスキップします。
