```
mutable struct TapTransformer <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    reactive_power_flow::Float64
    arc::Arc
    r::Float64
    x::Float64
    primary_shunt::Float64
    tap::Float64
    rating::Union{Nothing, Float64}
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A 2-winding transformer, with a tap changer for variable turns ratio.

The model uses an equivalent circuit assuming the impedance is on the High Voltage Side of the transformer. The model allocates the iron losses and magnetizing susceptance to the primary side

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `active_power_flow::Float64`: Initial condition of active power flow through the transformer (MW)
  * `reactive_power_flow::Float64`: Initial condition of reactive power flow through the transformer (MVAR)
  * `arc::Arc`: An [`Arc`](@ref) defining this transformer `from` a bus `to` another bus
  * `r::Float64`: Resistance in p.u. ([`SYSTEM_BASE`](@ref per_unit)), validation range: `(-2, 2)`
  * `x::Float64`: Reactance in p.u. ([`SYSTEM_BASE`](@ref per_unit)), validation range: `(-2, 4)`
  * `primary_shunt::Float64`: Shunt reactance in p.u. ([`SYSTEM_BASE`](@ref per_unit)), validation range: `(0, 2)`
  * `tap::Float64`: Normalized tap changer position for voltage control, varying between 0 and 2, with 1 centered at the nominal voltage, validation range: `(0, 2)`
  * `rating::Union{Nothing, Float64}`: Thermal rating (MVA). Flow through the transformer must be between -`rating`. When defining a transformer before it is attached to a `System`, `rating` must be in pu ([`SYSTEM_BASE`](@ref per_unit)) using the base power of the `System` it will be attached to, validation range: `(0, nothing)`
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
