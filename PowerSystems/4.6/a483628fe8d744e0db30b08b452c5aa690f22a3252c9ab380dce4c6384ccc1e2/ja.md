```julia
remove_component!(
    sys::PowerSystems.System,
    component::PowerSystems.Component
)

```

システムからその値によってコンポーネントを削除します。

コンポーネントが保存されていない場合はArgumentErrorをスローします。
