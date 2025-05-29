```julia
get_supplemental_attributes(
    _::Type{T<:InfrastructureSystems.SupplementalAttribute},
    component::InfrastructureSystems.InfrastructureSystemsComponent
) -> Any

```

補足属性のベクターを返します。Tは具体的または抽象的であり得ます。

# 引数

  * `T`: 補足属性の型
  * `supplemental_attributes::SupplementalAttributes`: システム内のSupplementalAttributes
  * `filter_func::Union{Nothing, Function} = nothing`: 型Tのコンポーネントを受け取り、Boolを返すオプションの関数。この関数を各コンポーネントに適用し、結果がtrueであるコンポーネントのみを返します。
