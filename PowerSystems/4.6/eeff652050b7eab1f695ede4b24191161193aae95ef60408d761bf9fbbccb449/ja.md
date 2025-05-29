```julia
set_shut_down!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, InfrastructureSystems.TimeSeriesData}
) -> Union{Float64, InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

`StaticInjection`デバイスのシャットダウンコストを`MarketBidCost`として、単一の数値または時系列に設定します。

# 引数

  * `sys::System`: PowerSystem System
  * `component::StaticInjection`: 静的インジェクションデバイス
  * `data::Union{Float64, IS.TimeSeriesData},`: データ。時系列の場合、eltypeは`Float64`でなければなりません。
