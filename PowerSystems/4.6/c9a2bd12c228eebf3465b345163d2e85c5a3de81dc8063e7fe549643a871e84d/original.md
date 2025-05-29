```julia
get_available_groups(
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

Like [`get_groups`](@ref get_groups(selector::ComponentSelector, sys::System)) but only operates on components for which [`get_available`](@ref) is `true`.
