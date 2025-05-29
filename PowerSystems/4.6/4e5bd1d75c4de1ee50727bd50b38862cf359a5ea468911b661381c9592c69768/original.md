```
mutable struct ConstantReserveGroup{T <: ReserveDirection} <: Service
    name::String
    available::Bool
    requirement::Float64
    ext::Dict{String, Any}
    contributing_services::Vector{Service}
    internal::InfrastructureSystemsInternal
end
```

A reserve product met by a group of individual reserves.

The group reserve requirement is added in addition to any individual reserve requirements, and devices that contribute to individual reserves within the group can also contribute to the overarching group reserve requirement. Example: A group of spinning and non-spinning reserves, where online generators providing spinning reserves can also contribute to the non-spinning reserve requirement.

This model has a constant procurement requirement, such as 3% of the system base power at all times. When defining the reserve, the `ReserveDirection` must be specified to define this as a [`ReserveUp`](@ref), [`ReserveDown`](@ref), or [`ReserveSymmetric`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `requirement::Float64`: the value of required reserves in p.u. ([`SYSTEM_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `contributing_services::Vector{Service}`: (default: `Vector{Service}()`) Services that contribute to this group requirement. Services must be added for this constraint to have an effect when conducting simulations in [`PowerSimulations.jl`](https://nrel-sienna.github.io/PowerSimulations.jl/latest/)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
