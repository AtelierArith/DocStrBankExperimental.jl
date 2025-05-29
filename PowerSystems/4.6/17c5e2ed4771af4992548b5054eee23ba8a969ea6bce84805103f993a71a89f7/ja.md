```julia
set_start_up!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}, InfrastructureSystems.TimeSeriesData}
) -> Union{Float64, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}, InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

`StaticInjection`デバイスのスタートアップコストを`MarketBidCost`として、単一の数値、単一の`StartUpStages`、または時系列のいずれかに設定します。

# 引数

  * `sys::System`: PowerSystem System
  * `component::StaticInjection`: 静的インジェクションデバイス
  * `data::Union{Float64, StartUpStages, IS.TimeSeriesData},`: データ。時系列の場合、`NTuple{3, Float64}`のeltypeでなければなりません。時系列の単一の値を表すには、`(value, 0.0, 0.0)`を使用します。
