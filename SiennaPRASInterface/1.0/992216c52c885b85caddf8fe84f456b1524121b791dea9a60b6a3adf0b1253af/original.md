# Arguments

  * `aggregation::Type{T} where T<:PowerSystems.AggregationTopology`: Level of aggregation to use for PRAS regions
  * `device_models::Array{SiennaPRASInterface.DeviceRAModel}`: DeviceRAModels to translate components into PRAS

The RATemplate contains all configuration necessary for building a PRAS Simulation from a PowerSystems.jl System.

Since PRAS is an area-based model, we provide a level of aggregation to apply.

PRAS models are processed in reverse order, with later models taking precedence.

# Example

```julia
template = RATemplate(
    PSY.Area,
    [
        DeviceRAModel(
            PSY.Generator,
            GeneratorPRAS(max_active_power="max_active_power"),
        ),
        DeviceRAModel(
            PSY.HydroEnergyReservoir,
            HydroEnergyReservoirPRAS(
                max_active_power="max_active_power",
                inflow="inflow",
                storage_capacity="storage_capacity",
            ),
        ),
    ],
)
```
