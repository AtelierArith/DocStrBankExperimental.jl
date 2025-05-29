```
mutable struct InterconnectingConverter <: StaticInjection
    name::String
    available::Bool
    bus::ACBus
    dc_bus::DCBus
    active_power::Float64
    rating::Float64
    active_power_limits::MinMax
    base_power::Float64
    dc_current::Float64
    max_dc_current::Float64
    loss_function::Union{LinearCurve, QuadraticCurve}
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

Interconnecting Power Converter (IPC) for transforming power from an ACBus to a DCBus

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bus::ACBus`: Bus on the AC side of this converter
  * `dc_bus::DCBus`: Bus on the DC side of this converter
  * `active_power::Float64`: Active power (MW) on the DC side, validation range: `active_power_limits`
  * `rating::Float64`: Maximum output power rating of the converter (MVA), validation range: `(0, nothing)`
  * `active_power_limits::MinMax`: Minimum and maximum stable active power levels (MW)
  * `base_power::Float64`: Base power of the converter in MVA, validation range: `(0, nothing)`
  * `dc_current::Float64`: (default: `0.0`) DC current (A) on the converter
  * `max_dc_current::Float64`: (default: `1e8`) Maximum stable dc current limits (A)
  * `loss_function::Union{LinearCurve, QuadraticCurve}`: (default: `LinearCurve(0.0)`) Linear or quadratic loss function with respect to the converter current
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
