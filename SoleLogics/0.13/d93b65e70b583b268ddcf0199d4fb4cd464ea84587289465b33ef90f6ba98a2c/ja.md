```
parseformula(
    T::Type{AnchoredFormula},
    expr::AbstractString,
    additional_operators::Union{Nothing,Vector{<:Operator}} = nothing;
    operators::Union{Nothing,Vector{<:Operator}},
    grammar::Union{Nothing,AbstractGrammar} = nothing,
    algebra::Union{Nothing,AbstractAlgebra} = nothing,
    kwargs...
)::AnchoredFormula
```

`AnchoredFormula`を返します。これは、[Shunting yard](https://en.wikipedia.org/wiki/Shunting_yard_algorithm)アルゴリズムを介して式を解析した結果です。デフォルトでは、この関数は`SoleLogics.BASE_PARSABLE_CONNECTIVES`にある演算子のみを解析できます。追加の演算子は、2番目の引数として提供できます。

関連する論理の`grammar`と`algebra`は、式で遭遇した演算子と`additional_operators`の演算子から`baseformula`関数を使用して推測されます。

[`parseformula`](@ref)、[`baseformula`](@ref)、[`BASE_PARSABLE_CONNECTIVES`](@ref)を参照してください。
