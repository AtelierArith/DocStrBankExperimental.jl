```julia
get_supplemental_attributes(
    filter_func::Function,
    _::Type{T<:InfrastructureSystems.SupplementalAttribute},
    mgr::InfrastructureSystems.SupplementalAttributeManager
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:InfrastructureSystems.SupplementalAttribute, I<:(Vector)}

```

補足属性のイテレータを返します。Tは具体的または抽象的であり得ます。配列が必要な場合は、結果に対してcollectを呼び出してください。

# 引数

  * `T`: 補足属性の型
  * `mgr::SupplementalAttributeManager`: システム内のSupplementalAttributeManager
  * `filter_func::Union{Nothing, Function} = nothing`: 型Tのコンポーネントを受け取り、Boolを返すオプションの関数。この関数を各コンポーネントに適用し、結果がtrueであるコンポーネントのみを返します。
