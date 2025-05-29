```
mutable struct DCBus <: Bus
    number::Int
    name::String
    magnitude::Union{Nothing, Float64}
    voltage_limits::Union{Nothing, MinMax}
    base_voltage::Union{Nothing, Float64}
    area::Union{Nothing, Area}
    load_zone::Union{Nothing, LoadZone}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A DC bus

# Arguments

  * `number::Int`: A unique bus identification number (positive integer)
  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `magnitude::Union{Nothing, Float64}`: voltage as a multiple of `base_voltage`, validation range: `voltage_limits`
  * `voltage_limits::Union{Nothing, MinMax}`: limits on the voltage variation as multiples of `base_voltage`
  * `base_voltage::Union{Nothing, Float64}`: the base voltage in kV, validation range: `(0, nothing)`
  * `area::Union{Nothing, Area}`: (default: `nothing`) the area containing the DC bus
  * `load_zone::Union{Nothing, LoadZone}`: (default: `nothing`) the load zone containing the DC bus
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
