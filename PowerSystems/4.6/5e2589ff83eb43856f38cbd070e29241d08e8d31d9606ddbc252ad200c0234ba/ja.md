```julia
get_components(
    scope_limiter::Union{Nothing, Function},
    selector::InfrastructureSystems.ComponentSelector,
    sys::PowerSystems.System
) -> Any

```

[`System`](@ref)を構成する[`ComponentSelector`](@ref)のコンポーネントを取得します。オプションで、考慮すべきコンポーネントを制限するために最初の引数としてフィルタ関数`scope_limiter`を指定できます。

# 引数

  * `scope_limiter::Union{Function, Nothing}`: [`ComponentSelector`](@ref)を参照
  * `selector::ComponentSelector`: 取得するコンポーネントの`ComponentSelector`
  * `sys::System`: コンポーネントを引き出すシステム
