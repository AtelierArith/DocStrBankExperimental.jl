```julia
add_time_series!(
    sys::PowerSystems.System,
    metadata_file::AbstractString;
    resolution
) -> Vector{InfrastructureSystems.TimeSeriesKey}

```

メタデータファイルまたはメタデータ記述子から時系列データを追加します。

# 引数

  * `sys::System`: システム
  * `metadata_file::AbstractString`: IS.TimeSeriesFileMetadata インスタンスの配列またはベクターを含む時系列のメタデータファイル。
  * `resolution::DateTime.Period=nothing`: この解像度に一致しない時系列をスキップします。
