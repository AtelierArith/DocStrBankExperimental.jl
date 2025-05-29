```
mutable struct Line <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    reactive_power_flow::Float64
    arc::Arc
    r::Float64
    x::Float64
    b::FromTo
    rating::Float64
    angle_limits::MinMax
    g::FromTo
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

An AC transmission line

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `active_power_flow::Float64`: Initial condition of active power flow on the line (MW)
  * `reactive_power_flow::Float64`: Initial condition of reactive power flow on the line (MVAR)
  * `arc::Arc`: An [`Arc`](@ref) defining this line `from` a bus `to` another bus
  * `r::Float64`: Resistance in pu ([`SYSTEM_BASE`](@ref per_unit)), validation range: `(0, 4)`
  * `x::Float64`: Reactance in pu ([`SYSTEM_BASE`](@ref per_unit)), validation range: `(0, 4)`
  * `b::FromTo`: Shunt susceptance in pu ([`SYSTEM_BASE`](@ref per_unit)), specified both on the `from` and `to` ends of the line. These are commonly modeled with the same value, validation range: `(0, 100)`
  * `rating::Float64`: Thermal rating (MVA). Flow on the line must be between -`rating` and `rating`. When defining a line before it is attached to a `System`, `rating` must be in pu ([`SYSTEM_BASE`](@ref per_unit)) using the base power of the `System` it will be attached to
  * `angle_limits::MinMax`: Minimum and maximum angle limits (radians), validation range: `(-1.571, 1.571)`
  * `g::FromTo`: (default: `(from=0.0, to=0.0)`) Shunt conductance in pu ([`SYSTEM_BASE`](@ref per_unit)), specified both on the `from` and `to` ends of the line. These are commonly modeled with the same value, validation range: `(0, 100)`
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
