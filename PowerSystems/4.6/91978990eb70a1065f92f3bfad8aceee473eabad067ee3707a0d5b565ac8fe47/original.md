```
mutable struct ACBus <: Bus
    number::Int
    name::String
    bustype::Union{Nothing, ACBusTypes}
    angle::Union{Nothing, Float64}
    magnitude::Union{Nothing, Float64}
    voltage_limits::Union{Nothing, MinMax}
    base_voltage::Union{Nothing, Float64}
    area::Union{Nothing, Area}
    load_zone::Union{Nothing, LoadZone}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

An AC bus

# Arguments

  * `number::Int`: A unique bus identification number (positive integer)
  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `bustype::Union{Nothing, ACBusTypes}`: Used to describe the connectivity and behavior of this bus. [Options are listed here.](@ref acbustypes_list)
  * `angle::Union{Nothing, Float64}`: angle of the bus in radians, validation range: `(-1.571, 1.571)`
  * `magnitude::Union{Nothing, Float64}`: voltage as a multiple of `base_voltage`, validation range: `voltage_limits`
  * `voltage_limits::Union{Nothing, MinMax}`: limits on the voltage variation as multiples of `base_voltage`
  * `base_voltage::Union{Nothing, Float64}`: the base voltage in kV, validation range: `(0, nothing)`
  * `area::Union{Nothing, Area}`: (default: `nothing`) the area containing the bus
  * `load_zone::Union{Nothing, LoadZone}`: (default: `nothing`) the load zone containing the bus
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
