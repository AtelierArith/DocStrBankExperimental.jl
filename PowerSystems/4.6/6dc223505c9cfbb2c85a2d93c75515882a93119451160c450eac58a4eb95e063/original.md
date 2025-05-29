```julia
get_existing_component_types(
    sys::PowerSystems.System
) -> Vector{DataType}

```

Return all the component types in the system. It does not return masked components.
