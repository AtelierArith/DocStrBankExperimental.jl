```julia
get_available_component(
    scope_limiter::Union{Nothing, Function},
    selector::InfrastructureSystems.SingularComponentSelector,
    sys::PowerSystems.System
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

[`get_component`](@ref get_component(     scope_limiter::Union{Function, Nothing},     selector::IS.SingularComponentSelector,     sys::System, ))と同様ですが、[`get_available`](@ref)が`true`であるコンポーネントのみに対して操作します。
