```julia
set_no_load_cost!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, InfrastructureSystems.TimeSeriesData}
) -> Union{Float64, InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

`StaticInjection`デバイスのノーロードコストをスカラーまたはタイムシリーズに設定します。

# 引数

  * `sys::System`: PowerSystemシステム
  * `component::StaticInjection`: 静的インジェクションデバイス
  * `time_series_data::Union{Float64, IS.TimeSeriesData},`: データ。タイムシリーズの場合、eltypeは`Float64`でなければなりません。
