```
mutable struct AreaInterchange <: Branch
    name::String
    available::Bool
    active_power_flow::Float64
    from_area::Area
    to_area::Area
    flow_limits::FromTo_ToFrom
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

Flow exchanged between Areas. This Interchange is agnostic to the lines connecting the areas. It does not substitute Interface which is the total flow across a group of lines

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `active_power_flow::Float64`: Initial condition of active power flow on the line (MW)
  * `from_area::Area`: Area from which the power is extracted
  * `to_area::Area`: Area to which the power is injected
  * `flow_limits::FromTo_ToFrom`: Max flow between the areas. It ignores lines and other branches totals
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
