```julia
get_available_component(
    selector::InfrastructureSystems.SingularComponentSelector,
    sys::PowerSystems.System
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

[`get_component`](@ref get_component(     selector::IS.SingularComponentSelector,     sys::System, ))と同様ですが、[`get_available`](@ref)が`true`であるコンポーネントのみに対して操作します。
