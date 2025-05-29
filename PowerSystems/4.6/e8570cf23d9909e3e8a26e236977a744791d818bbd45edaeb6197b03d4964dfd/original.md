```
mutable struct ThermalStandard <: ThermalGen
    name::String
    available::Bool
    status::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    active_power_limits::MinMax
    reactive_power_limits::Union{Nothing, MinMax}
    ramp_limits::Union{Nothing, UpDown}
    operation_cost::Union{ThermalGenerationCost, MarketBidCost}
    base_power::Float64
    time_limits::Union{Nothing, UpDown}
    must_run::Bool
    prime_mover_type::PrimeMovers
    fuel::ThermalFuels
    services::Vector{Service}
    time_at_status::Float64
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A thermal generator, such as a fossil fuel and nuclear generator.

This is a standard representation with options to include a minimum up time, minimum down time, and ramp limits. For a more detailed representation the start-up and shut-down processes, including hot starts, see [`ThermalMultiStart`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `status::Bool`: Initial commitment condition at the start of a simulation (`true` = on or `false` = off)
  * `bus::ACBus`: Bus that this component is connected to
  * `active_power::Float64`: Initial active power set point of the unit in MW. For power flow, this is the steady state operating point of the system. For production cost modeling, this may or may not be used as the initial starting point for the solver, depending on the solver used, validation range: `active_power_limits`
  * `reactive_power::Float64`: Initial reactive power set point of the unit (MVAR), validation range: `reactive_power_limits`
  * `rating::Float64`: Maximum output power rating of the unit (MVA), validation range: `(0, nothing)`
  * `active_power_limits::MinMax`: Minimum and maximum stable active power levels (MW), validation range: `(0, nothing)`
  * `reactive_power_limits::Union{Nothing, MinMax}`: Minimum and maximum reactive power limits. Set to `Nothing` if not applicable
  * `ramp_limits::Union{Nothing, UpDown}`: ramp up and ramp down limits in MW/min, validation range: `(0, nothing)`
  * `operation_cost::Union{ThermalGenerationCost, MarketBidCost}`: [`OperationalCost`](@ref) of generation
  * `base_power::Float64`: Base power of the unit (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `time_limits::Union{Nothing, UpDown}`: (default: `nothing`) Minimum up and Minimum down time limits in hours, validation range: `(0, nothing)`
  * `must_run::Bool`: (default: `false`) Set to `true` if the unit is must run
  * `prime_mover_type::PrimeMovers`: (default: `PrimeMovers.OT`) Prime mover technology according to EIA 923. Options are listed [here](@ref pm_list)
  * `fuel::ThermalFuels`: (default: `ThermalFuels.OTHER`) Prime mover fuel according to EIA 923. Options are listed [here](@ref tf_list)
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `time_at_status::Float64`: (default: `INFINITE_TIME`) Time (e.g., `Hours(6)`) the generator has been on or off, as indicated by `status`
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
