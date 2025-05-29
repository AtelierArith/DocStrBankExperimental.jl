```
mutable struct StandardLoad <: StaticLoad
    name::String
    available::Bool
    bus::ACBus
    base_power::Float64
    constant_active_power::Float64
    constant_reactive_power::Float64
    impedance_active_power::Float64
    impedance_reactive_power::Float64
    current_active_power::Float64
    current_reactive_power::Float64
    max_constant_active_power::Float64
    max_constant_reactive_power::Float64
    max_impedance_active_power::Float64
    max_impedance_reactive_power::Float64
    max_current_active_power::Float64
    max_current_reactive_power::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A voltage-dependent [ZIP load](@ref Z), most commonly used for dynamics modeling.

A `StandardLoad` breaks the ZIP into three pieces: Z (constant impedance), I (constant current), and P (constant power), according to `P = P_P * V^0 + P_I * V^1 + P_Z * V^2` for active power and `Q = Q_P * V^0 + Q_I * V^1 + Q_Z * V^2` for reactive power. (Voltage V is in per unit.)

For an alternative exponential formulation of the ZIP model, see [`ExponentialLoad`](@ref). For a simpler load model with no voltage dependency, see [`PowerLoad`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bus::ACBus`: Bus that this component is connected to
  * `base_power::Float64`: Base power of the load (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `constant_active_power::Float64`: (default: `0.0`) Constant active power demand in MW (P_P)
  * `constant_reactive_power::Float64`: (default: `0.0`) Constant reactive power demand in MVAR (Q_P)
  * `impedance_active_power::Float64`: (default: `0.0`) Active power coefficient in MW for constant impedance load (P_Z)
  * `impedance_reactive_power::Float64`: (default: `0.0`) Reactive power coefficient in MVAR for constant impedance load (Q_Z)
  * `current_active_power::Float64`: (default: `0.0`) Active power coefficient in MW for constant current load (P_I)
  * `current_reactive_power::Float64`: (default: `0.0`) Reactive power coefficient in MVAR for constant current load (Q_I)
  * `max_constant_active_power::Float64`: (default: `0.0`) Maximum active power (MW) drawn by constant power load
  * `max_constant_reactive_power::Float64`: (default: `0.0`) Maximum reactive power (MVAR) drawn by constant power load
  * `max_impedance_active_power::Float64`: (default: `0.0`) Maximum active power (MW) drawn by constant impedance load
  * `max_impedance_reactive_power::Float64`: (default: `0.0`) Maximum reactive power (MVAR) drawn by constant impedance load
  * `max_current_active_power::Float64`: (default: `0.0`) Maximum active power (MW) drawn by constant current load
  * `max_current_reactive_power::Float64`: (default: `0.0`) Maximum reactive power (MVAR) drawn by constant current load
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
