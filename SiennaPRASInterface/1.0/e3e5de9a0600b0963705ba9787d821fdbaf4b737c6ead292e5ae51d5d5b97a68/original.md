```julia
DeviceRAModel(
    ::Type{D<:PowerSystems.Device},
    ::Type{B<:SiennaPRASInterface.AbstractRAFormulation};
    time_series_names,
    kwargs...
) -> SiennaPRASInterface.DeviceRAModel

```

# Arguments

  * `::Type{D}`: Device type
  * `::Type{B}`: Formulation type
  * `time_series_names::Dict{Symbol, String}`: Mapping of time series `Symbol` to names
  * `kwargs...`: Additional arguments to pass to the formulation constructor

Keyword arguments in DeviceRAModel are passed to the formulation constructor.

You may also pass a `time_series_names` Dict to map time series `Symbol` to names.

# Example

```julia
DeviceRAModel(
    PSY.Generator,
    GeneratorPRAS(max_active_power="max_active_power"),
)
```

```julia
DeviceRAModel(
    PSY.HydroEnergyReservoir,
    HydroEnergyReservoirPRAS;
    max_active_power="max_active_power",
    inflow="inflow",
    storage_capacity="storage_capacity",
)
```

```julia
DeviceRAModel(
    PSY.HybridSystem,
    HybridSystemPRAS;
    time_series_names=Dict(:max_active_power="max_active_power"),
)
```
