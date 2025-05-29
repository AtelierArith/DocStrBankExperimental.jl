```julia
set_incremental_initial_input!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, InfrastructureSystems.TimeSeriesData}
) -> Union{InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

`StaticInjection`デバイスの`MarketBidCost`の`incremental_initial_input`をスカラーまたは時系列に設定します。

# 引数

  * `sys::System`: PowerSystem System
  * `component::StaticInjection`: 静的インジェクションデバイス
  * `time_series_data::Union{Float64, IS.TimeSeriesData},`: データ。時系列の場合、eltypeは`Float64`でなければなりません。
