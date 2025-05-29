```julia
System(
    data::PowerSystems.PowerSystemTableData;
    time_series_resolution,
    time_series_in_memory,
    time_series_directory,
    runchecks,
    kwargs...
) -> PowerSystems.System

```

PowerSystemTableDataデータからSystemを構築します。

# 引数

  * `time_series_resolution::Union{DateTime, Nothing}=nothing`: この解像度に一致するtime_seriesのみを保存します。
  * `time_series_in_memory::Bool=false`: HDF5ファイルの代わりにメモリに時系列データを保存します。
  * `time_series_directory=nothing`: tmpfsの代わりにディレクトリに時系列データを保存します。
  * `runchecks::Bool=true`: 構造体のフィールドを検証します。

複数の解像度を持つtime_seriesが検出された場合、DataFormatErrorをスローします。

  * time_seriesが他のものとは異なる解像度を持っています。
  * time_seriesが他のものとは異なるホライズンを持っています。
