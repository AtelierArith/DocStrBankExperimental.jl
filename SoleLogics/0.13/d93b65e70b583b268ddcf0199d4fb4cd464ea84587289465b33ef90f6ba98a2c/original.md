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

Return a `AnchoredFormula` which is the result of parsing an expression via the [Shunting yard](https://en.wikipedia.org/wiki/Shunting_yard_algorithm) algorithm. By default, this function is only able to parse operators in `SoleLogics.BASE_PARSABLE_CONNECTIVES`; additional operators may be provided as a second argument.

The `grammar` and `algebra` of the associated logic is inferred using the `baseformula` function from the operators encountered in the expression, and those in `additional_operators`.

See [`parseformula`](@ref), [`baseformula`](@ref), [`BASE_PARSABLE_CONNECTIVES`](@ref).
