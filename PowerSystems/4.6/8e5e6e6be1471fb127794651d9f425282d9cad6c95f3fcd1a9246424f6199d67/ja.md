```julia
remove_supplemental_attribute!(
    sys::PowerSystems.System,
    component::PowerSystems.Component,
    attribute::InfrastructureSystems.SupplementalAttribute
)

```

コンポーネントから補足属性を削除します。属性が他のコンポーネントに接続されていない場合、システムからも削除されます。
