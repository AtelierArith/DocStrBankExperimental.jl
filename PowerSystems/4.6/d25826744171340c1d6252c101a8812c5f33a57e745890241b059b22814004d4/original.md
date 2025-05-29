```julia
get_available_components(
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

Like [`get_components`](@ref get_components(selector::ComponentSelector, sys::System)) but only operates on components for which [`get_available`](@ref) is `true`.
