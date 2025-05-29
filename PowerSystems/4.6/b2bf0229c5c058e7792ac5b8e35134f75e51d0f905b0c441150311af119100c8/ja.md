```julia
get_supplemental_attribute(
    sys::PowerSystems.System,
    uuid::Base.UUID
) -> InfrastructureSystems.SupplementalAttribute

```

指定されたuuidを持つ補足属性を返します。

属性が保存されていない場合はArgumentErrorをスローします。
