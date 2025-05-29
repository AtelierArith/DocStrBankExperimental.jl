```
mutable struct LoadZone <: AggregationTopology
    name::String
    peak_active_power::Float64
    peak_reactive_power::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A load zone for electricity price analysis.

The load zone can be specified when defining each [`ACBus`](@ref) or [`DCBus`](@ref) in the zone

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `peak_active_power::Float64`: Peak active power in the zone (MW)
  * `peak_reactive_power::Float64`: Peak reactive power in the zone (MVAR)
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
