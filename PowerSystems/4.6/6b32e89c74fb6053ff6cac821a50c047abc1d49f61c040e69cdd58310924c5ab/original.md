```
mutable struct TwoTerminalVSCDCLine <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    arc::Arc
    rectifier_tap_limits::MinMax
    rectifier_xrc::Float64
    rectifier_firing_angle::MinMax
    inverter_tap_limits::MinMax
    inverter_xrc::Float64
    inverter_extinction_angle::MinMax
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A Voltage Sourced Converter (VSC)-HVDC transmission line.

As implemented in ["Power System Modelling and Scripting"](https://link.springer.com/book/10.1007/978-3-642-13669-6) by Federico Milano, Chapter 18, Page 397. This model is suitable for dynamic simulations

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `active_power_flow::Float64`: Initial condition of active power flow on the line (MW)
  * `arc::Arc`: An [`Arc`](@ref) defining this line `from` a bus `to` another bus
  * `rectifier_tap_limits::MinMax`: Minimum and maximum rectifier tap limits as a ratio between the primary and secondary side voltages
  * `rectifier_xrc::Float64`: Rectifier commutation reactance in p.u. ([`DEVICE_BASE`](@ref per_unit))
  * `rectifier_firing_angle::MinMax`: Minimum and maximum rectifier firing angle (α) (radians)
  * `inverter_tap_limits::MinMax`: Minimum and maximum inverter tap limits as a ratio between the primary and secondary side voltages
  * `inverter_xrc::Float64`: Inverter commutation reactance in p.u. ([`DEVICE_BASE`](@ref per_unit))
  * `inverter_extinction_angle::MinMax`: Minimum and maximum inverter extinction angle (γ) (radians)
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
