```julia
set_fuel_cost!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, InfrastructureSystems.TimeSeriesData}
) -> Any

```

コンポーネントの変動コストの燃料コストを設定します。これは `FuelCurve` でなければなりません。
