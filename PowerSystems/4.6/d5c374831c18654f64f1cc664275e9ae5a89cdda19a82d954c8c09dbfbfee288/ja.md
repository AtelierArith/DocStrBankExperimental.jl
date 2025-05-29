```julia
get_components(
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

[`ComponentSelector`](@ref)を構成する[`System`](@ref)のコンポーネントを取得します。

# 引数

  * `selector::ComponentSelector`: 取得するコンポーネントの`ComponentSelector`
  * `sys::System`: コンポーネントを引き出すシステム
