```julia
get_available_groups(
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

[`get_groups`](@ref get_groups(selector::ComponentSelector, sys::System))と同様ですが、[`get_available`](@ref)が`true`であるコンポーネントのみに対して操作します。
