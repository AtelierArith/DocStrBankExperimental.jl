```julia
set_variable_cost!(
    _::PowerSystems.System,
    component::PowerSystems.ReserveDemandCurve,
    data::InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}
) -> InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}

```

Adds fixed energy market bids to the ReserveDemandCurve.

# Arguments

  * `sys::System`: PowerSystem System
  * `component::ReserveDemandCurve`: the curve
  * `time*series*data::CostCurve{PiecewiseIncrementalCurve}
