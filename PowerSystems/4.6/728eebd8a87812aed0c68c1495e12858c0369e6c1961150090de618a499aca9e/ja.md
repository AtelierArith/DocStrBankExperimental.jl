```julia
remove_component_from_subsystem!(
    sys::PowerSystems.System,
    subsystem_name::AbstractString,
    component::PowerSystems.Component
)

```

サブシステムからコンポーネントを削除します。

サブシステム名またはコンポーネントが保存されていない場合、ArgumentErrorをスローします。
