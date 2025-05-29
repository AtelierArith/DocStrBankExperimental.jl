```julia
component_to_qualified_string(
    component_type::Type{<:InfrastructureSystems.InfrastructureSystemsComponent},
    component_name::AbstractString
) -> Any

```

Canonical way to turn an `InfrastructureSystemsComponent` specification/instance into a unique-per-system string.
