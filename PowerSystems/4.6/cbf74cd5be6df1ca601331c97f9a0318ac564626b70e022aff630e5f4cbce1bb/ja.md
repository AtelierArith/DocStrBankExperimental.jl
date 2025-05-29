```julia
validate_component_with_system(
    component::PowerSystems.Component,
    sys::PowerSystems.System
) -> Bool

```

システムデータに対してコンポーネントを検証します。インスタンスが有効な場合はtrueを返します。

インスタンス内に含まれるデータのみを必要とする検証ロジックの場合は、[`validate_component`](@ref)を参照してください。
