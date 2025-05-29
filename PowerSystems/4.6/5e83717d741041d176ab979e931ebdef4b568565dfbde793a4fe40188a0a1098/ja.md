```julia
set_decremental_variable_cost!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesData},
    power_units::InfrastructureSystems.UnitSystemModule.UnitSystem
)

```

`StaticInjection`デバイスのための減少的変数コスト入札を`MarketBidCost`で設定します。

# 引数

  * `sys::System`: PowerSystemシステム
  * `component::StaticInjection`: 静的注入デバイス
  * `time_series_data::Union{Nothing, IS.TimeSeriesData, CostCurve{PiecewiseIncrementalCurve}},`: データ。タイムシリーズを使用する場合、`PiecewiseStepData`のeltypeでなければなりません。`PiecewiseIncrementalCurve`は単一のCostCurveにのみ受け入れられ、タイムシリーズデータには受け入れられません。
  * `power_units::UnitSystem`: データに使用される単位。
