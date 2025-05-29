```julia
set_fuel_cost!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, InfrastructureSystems.TimeSeriesData}
) -> Any

```

Set the fuel cost of the component's variable cost, which must be a `FuelCurve`.
