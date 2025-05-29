```
mutable struct TModelHVDCLine <: DCBranch
    name::String
    available::Bool
    active_power_flow::Float64
    arc::Arc
    r::Float64
    l::Float64
    c::Float64
    active_power_limits_from::MinMax
    active_power_limits_to::MinMax
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A High Voltage DC transmission line for modeling DC transmission networks.

This line must be connected to a [`DCBus`](@ref) on each end. It uses a T-Model of the line impedance. This is suitable for operational simulations with a multi-terminal DC network

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `active_power_flow::Float64`: Initial condition of active power flow on the line (MW)
  * `arc::Arc`: An [`Arc`](@ref) defining this line `from` a bus `to` another bus
  * `r::Float64`: Total series Resistance in p.u. ([`SYSTEM_BASE`](@ref per_unit)), split equally on both sides of the shunt capacitance
  * `l::Float64`: Total series Inductance in p.u. ([`SYSTEM_BASE`](@ref per_unit)), split equally on both sides of the shunt capacitance
  * `c::Float64`: Shunt capacitance in p.u. ([`SYSTEM_BASE`](@ref per_unit))
  * `active_power_limits_from::MinMax`: Minimum and maximum active power flows to the FROM node (MW)
  * `active_power_limits_to::MinMax`: Minimum and maximum active power flows to the TO node (MW)
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
