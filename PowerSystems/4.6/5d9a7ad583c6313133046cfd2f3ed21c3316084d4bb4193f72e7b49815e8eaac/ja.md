```julia
get_component(
    selector::InfrastructureSystems.SingularComponentSelector,
    sys::PowerSystems.System
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

[`System`](@ref)を構成する[`SingularComponentSelector`](@ref)のコンポーネントを取得します。存在しない場合は`nothing`を返します。

# 引数

  * `selector::SingularComponentSelector`: 取得するコンポーネントの`SingularComponentSelector`
  * `sys::System`: コンポーネントを取得するシステム
