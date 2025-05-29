```julia
get_available_groups(
    scope_limiter::Union{Nothing, Function},
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

Like [`get_groups`](@ref get_groups(     scope_limiter::Union{Function, Nothing},     selector::ComponentSelector,     sys::System, )) but only operates on components for which [`get_available`](@ref) is `true`.
