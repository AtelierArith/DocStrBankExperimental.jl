```
mutable struct ExponentialLoad <: StaticLoad
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    α::Float64
    β::Float64
    base_power::Float64
    max_active_power::Float64
    max_reactive_power::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A voltage-dependent [ZIP load](@ref Z), most commonly used for dynamics modeling.

An `ExponentialLoad` models active power as P = P0 * V^α and reactive power as Q = Q0 * V^β, where the exponents α and β select govern the voltage dependency. For an alternative three-part formulation of the ZIP model, see [`StandardLoad`](@ref). For a simpler load model with no voltage dependency, see [`PowerLoad`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bus::ACBus`: Bus that this component is connected to
  * `active_power::Float64`: Active power coefficient, P0 (MW)
  * `reactive_power::Float64`: Reactive power coefficient, Q0 (MVAR)
  * `α::Float64`: Exponent relating voltage dependency for active power. 0 = constant power only, 1 = constant current only, and 2 = constant impedance only, validation range: `(0, nothing)`
  * `β::Float64`: Exponent relating voltage dependency for reactive power. 0 = constant power only, 1 = constant current only, and 2 = constant impedance only, validation range: `(0, nothing)`
  * `base_power::Float64`: Base power (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `max_active_power::Float64`: Maximum active power (MW) that this load can demand
  * `max_reactive_power::Float64`: Maximum reactive power (MVAR) that this load can demand
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
