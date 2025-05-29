```julia
get_groups(
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

[`ComponentSelector`](@ref)を構成するグループを取得します。

# 引数

  * `selector::ComponentSelector`: 取得するグループの`ComponentSelector`
  * `sys::System`: コンポーネントを引き出すシステム
