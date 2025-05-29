```
mutable struct HydroEnergyReservoir <: HydroGen
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    prime_mover_type::PrimeMovers
    active_power_limits::MinMax
    reactive_power_limits::Union{Nothing, MinMax}
    ramp_limits::Union{Nothing, UpDown}
    time_limits::Union{Nothing, UpDown}
    base_power::Float64
    storage_capacity::Float64
    inflow::Float64
    initial_storage::Float64
    operation_cost::Union{HydroGenerationCost, StorageCost, MarketBidCost}
    storage_target::Float64
    conversion_factor::Float64
    status::Bool
    time_at_status::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A hydropower generator with an upper reservoir, offering some energy storage and operational flexibility.

For hydro generators with pumped storage, see [`HydroPumpedStorage`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bus::ACBus`: Bus that this component is connected to
  * `active_power::Float64`: Initial active power set point of the unit in MW. For power flow, this is the steady state operating point of the system. For production cost modeling, this may or may not be used as the initial starting point for the solver, depending on the solver used
  * `reactive_power::Float64`: Initial reactive power set point of the unit (MVAR), validation range: `reactive_power_limits`
  * `rating::Float64`: Maximum output power rating of the unit (MVA), validation range: `(0, nothing)`
  * `prime_mover_type::PrimeMovers`: Prime mover technology according to EIA 923. Options are listed [here](@ref pm_list)
  * `active_power_limits::MinMax`: Minimum and maximum stable active power levels (MW)
  * `reactive_power_limits::Union{Nothing, MinMax}`: Minimum and maximum reactive power limits. Set to `Nothing` if not applicable
  * `ramp_limits::Union{Nothing, UpDown}`: ramp up and ramp down limits in MW/min, validation range: `(0, nothing)`
  * `time_limits::Union{Nothing, UpDown}`: Minimum up and Minimum down time limits in hours, validation range: `(0, nothing)`
  * `base_power::Float64`: Base power of the unit (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `storage_capacity::Float64`: Maximum storage capacity in the reservoir (units can be p.u-hr or m^3), validation range: `(0, nothing)`
  * `inflow::Float64`: Baseline inflow into the reservoir (units can be p.u. or m^3/hr), validation range: `(0, nothing)`
  * `initial_storage::Float64`: Initial storage capacity in the reservoir (units can be p.u-hr or m^3), validation range: `(0, nothing)`
  * `operation_cost::Union{HydroGenerationCost, StorageCost, MarketBidCost}`: (default: `HydroGenerationCost(nothing)`) [`OperationalCost`](@ref) of generation
  * `storage_target::Float64`: (default: `1.0`) Storage target at the end of simulation as a fraction of storage capacity
  * `conversion_factor::Float64`: (default: `1.0`) Conversion factor from flow/volume to energy: m^3 -> p.u-hr
  * `status::Bool`: (default: `false`) Initial commitment condition at the start of a simulation (`true` = on or `false` = off)
  * `time_at_status::Float64`: (default: `INFINITE_TIME`) Time (e.g., `Hours(6)`) the generator has been on or off, as indicated by `status`
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
