```
mutable struct ConstantReserve{T <: ReserveDirection} <: Reserve{T}
    name::String
    available::Bool
    time_frame::Float64
    requirement::Float64
    sustained_time::Float64
    max_output_fraction::Float64
    max_participation_factor::Float64
    deployed_fraction::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A reserve product with a constant procurement requirement, such as 3% of the system base power at all times.

This reserve product includes online generators that can respond right away after an unexpected contingency, such as a transmission line or generator outage. When defining the reserve, the `ReserveDirection` must be specified to define this as a [`ReserveUp`](@ref), [`ReserveDown`](@ref), or [`ReserveSymmetric`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `time_frame::Float64`: the saturation time_frame in minutes to provide reserve contribution, validation range: `(0, nothing)`
  * `requirement::Float64`: the value of required reserves in p.u. ([`SYSTEM_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `sustained_time::Float64`: (default: `3600.0`) the time in seconds reserve contribution must sustained at a specified level, validation range: `(0, nothing)`
  * `max_output_fraction::Float64`: (default: `1.0`) the maximum fraction of each device's output that can be assigned to the service, validation range: `(0, 1)`
  * `max_participation_factor::Float64`: (default: `1.0`) the maximum portion [0, 1.0] of the reserve that can be contributed per device, validation range: `(0, 1)`
  * `deployed_fraction::Float64`: (default: `0.0`) Fraction of service procurement that is assumed to be actually deployed. Most commonly, this is assumed to be either 0.0 or 1.0, validation range: `(0, 1)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
