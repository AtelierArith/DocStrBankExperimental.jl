```julia
get_components_by_name(
    _::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System,
    name::AbstractString
) -> Vector{T} where T<:InfrastructureSystems.InfrastructureSystemsComponent

```

Get the components of abstract type T with name. Note that PowerSystems enforces unique names on each concrete type but not across concrete types.

See [`get_component`](@ref) if the concrete type is known.

Throws ArgumentError if T is not an abstract type.
