```julia
get_component(
    scope_limiter::Union{Nothing, Function},
    selector::InfrastructureSystems.SingularComponentSelector,
    sys::PowerSystems.System
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

[`System`](@ref)を構成する[`SingularComponentSelector`](@ref)のコンポーネントを取得します。存在しない場合は`nothing`を返します。考慮すべきコンポーネントを制限するために、最初の引数としてフィルタ関数`scope_limiter`をオプションで指定できます。

# 引数

  * `scope_limiter::Union{Function, Nothing}`: [`ComponentSelector`](@ref)を参照
  * `selector::SingularComponentSelector`: 取得するコンポーネントの`SingularComponentSelector`
  * `sys::System`: コンポーネントを引き出すシステム
