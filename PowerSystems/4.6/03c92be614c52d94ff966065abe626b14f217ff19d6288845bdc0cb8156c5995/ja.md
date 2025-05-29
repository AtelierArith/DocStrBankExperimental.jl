```julia
set_variable_cost!(
    _::PowerSystems.System,
    component::PowerSystems.ReserveDemandCurve,
    data::InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}
) -> InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}

```

ReserveDemandCurveに固定エネルギー市場入札を追加します。

# 引数

  * `sys::System`: PowerSystem システム
  * `component::ReserveDemandCurve`: 曲線
  * `time*series*data::CostCurve{PiecewiseIncrementalCurve}
