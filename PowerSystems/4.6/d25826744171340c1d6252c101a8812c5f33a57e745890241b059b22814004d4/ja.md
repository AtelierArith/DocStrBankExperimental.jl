```julia
get_available_components(
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

[`get_components`](@ref get_components(selector::ComponentSelector, sys::System))と同様ですが、[`get_available`](@ref)が`true`であるコンポーネントのみに対して操作します。
