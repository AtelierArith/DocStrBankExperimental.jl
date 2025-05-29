```julia
get_component(
    _::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System,
    name::AbstractString
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

Get the component of type T with name. Returns nothing if no component matches. If T is an abstract type then the names of components across all subtypes of T must be unique.

See [`get_components_by_name`](@ref) for abstract types with non-unique names across subtypes.

Throws ArgumentError if T is not a concrete type and there is more than one component with     requested name
