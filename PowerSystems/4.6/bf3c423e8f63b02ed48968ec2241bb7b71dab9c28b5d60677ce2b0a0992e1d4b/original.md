```
mutable struct PowerLoad <: StaticLoad
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    base_power::Float64
    max_active_power::Float64
    max_reactive_power::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A [static](@ref S) power load, most commonly used for operational models such as power flow and operational optimizations.

This load consumes a set amount of power (set by `active_power` for a power flow simulation or a `max_active_power` time series for an operational simulation). For loads that can be compensated for load interruptions through demand response programs, see [`InterruptiblePowerLoad`](@ref). For voltage-dependent loads used in [dynamics](@ref D) modeling, see [`StandardLoad`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bus::ACBus`: Bus that this component is connected to
  * `active_power::Float64`: Initial steady-state active power demand (MW)
  * `reactive_power::Float64`: Initial steady-state reactive power demand (MVAR)
  * `base_power::Float64`: Base power (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `max_active_power::Float64`: Maximum active power (MW) that this load can demand
  * `max_reactive_power::Float64`: Maximum reactive power (MVAR) that this load can demand
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
