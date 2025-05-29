```
mutable struct Area <: AggregationTopology
    name::String
    peak_active_power::Float64
    peak_reactive_power::Float64
    load_response::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A collection of buses for control purposes.

The `Area` can be specified when defining each [`ACBus`](@ref) or [`DCBus`](@ref) in the area

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `peak_active_power::Float64`: (default: `0.0`) Peak active power in the area
  * `peak_reactive_power::Float64`: (default: `0.0`) Peak reactive power in the area
  * `load_response::Float64`: (default: `0.0`) Load-frequency damping parameter modeling how much the load in the area changes due to changes in frequency (MW/Hz). [Example here.](https://doi.org/10.1109/NAPS50074.2021.9449687)
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
