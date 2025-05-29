```
parseformula(
    T::Type{AnchoredFormula},
    expr::String,
    additional_operators::Union{Nothing,Vector{<:Operator}} = nothing;
    operators::Union{Nothing,Vector{<:Operator}},
    grammar::Union{Nothing,AbstractGrammar} = nothing,
    algebra::Union{Nothing,AbstractAlgebra} = nothing,
    kwargs...
)::AnchoredFormula
```

与えられた式を[シュンティングヤード](https://en.wikipedia.org/wiki/Shunting_yard_algorithm)アルゴリズムを介して解析することによって得られる`AnchoredFormula`を返します。デフォルトでは、この関数は`SoleLogics.BASE_PARSABLE_CONNECTIVES`にある演算子のみを解析できます。追加の演算子は第二引数として提供できます。

関連する論理の`grammar`と`algebra`は、式内で遭遇した演算子と`additional_operators`内の演算子から`baseformula`関数を使用して推測されます。

[`parseformula`](@ref)、[`baseformula`](@ref)、[`BASE_PARSABLE_CONNECTIVES`](@ref)を参照してください。
