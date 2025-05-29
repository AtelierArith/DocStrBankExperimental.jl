```julia
set_decremental_initial_input!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, InfrastructureSystems.TimeSeriesData}
) -> Union{InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

`StaticInjection`デバイスの`MarketBidCost`に対して、スカラーまたは時系列のいずれかに`decremental_initial_input`を設定します。

# 引数

  * `sys::System`: PowerSystemシステム
  * `component::StaticInjection`: 静的注入デバイス
  * `time_series_data::Union{Float64, IS.TimeSeriesData},`: データ。時系列の場合、eltypeは`Float64`でなければなりません。
