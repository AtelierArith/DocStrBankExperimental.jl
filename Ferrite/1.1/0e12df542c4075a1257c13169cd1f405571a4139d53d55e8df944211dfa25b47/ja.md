```
FacetQuadratureRule{shape}([::Type{T},] [quad_rule_type::Symbol,] order::Int)
FacetQuadratureRule{shape}(facet_rules::NTuple{<:Any, <:QuadratureRule{shape}})
FacetQuadratureRule{shape}(facet_rules::AbstractVector{<:QuadratureRule{shape}})
```

`shape`のファセットの積分に使用される`FacetQuadratureRule`を作成します（タイプ[`AbstractRefShape`](@ref)の）。`order`は数値積分ルールの次数です。シンボルが提供されていない場合、各ファセットの参照形状のデフォルトの`quad_rule_type`が使用されます（[QuadratureRule](@ref)を参照）。混合ファセットタイプ（例：`RefPrism`と`RefPyramid`）を持つセルの非デフォルトの`quad_rule_type`の場合、`facet_rules`を明示的に提供する必要があります。

`FacetQuadratureRule`は[`FacetValues`](@ref)を作成するためのコンポーネントの1つとして使用されます。
