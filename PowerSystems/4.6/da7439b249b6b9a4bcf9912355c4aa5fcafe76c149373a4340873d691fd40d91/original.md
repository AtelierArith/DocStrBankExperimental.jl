```julia
get_available_component(
    scope_limiter::Union{Nothing, Function},
    selector::InfrastructureSystems.SingularComponentSelector,
    sys::PowerSystems.System
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

Like [`get_component`](@ref get_component(     scope_limiter::Union{Function, Nothing},     selector::IS.SingularComponentSelector,     sys::System, )) but only operates on components for which [`get_available`](@ref) is `true`.
