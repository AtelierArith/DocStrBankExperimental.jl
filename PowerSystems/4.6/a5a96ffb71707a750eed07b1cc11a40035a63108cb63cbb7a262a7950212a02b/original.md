```
mutable struct FixedAdmittance <: ElectricLoad
    name::String
    available::Bool
    bus::ACBus
    Y::Complex{Float64}
    dynamic_injector::Union{Nothing, DynamicInjection}
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A fixed admittance.

Most often used in dynamics or AC power flow studies as a source of reactive power

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bus::ACBus`: Bus that this component is connected to
  * `Y::Complex{Float64}`: Fixed admittance in p.u. ([`SYSTEM_BASE`](@ref per_unit))
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection model for admittance
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
