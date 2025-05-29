```julia
is_assigned_to_subsystem(
    sys::PowerSystems.System,
    component::PowerSystems.Component,
    subsystem_name::AbstractString
) -> Bool

```

コンポーネントがサブシステムに割り当てられている場合はtrueを返します。
