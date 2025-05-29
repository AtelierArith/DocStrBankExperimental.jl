```julia
read_realized_expression(
    res::PowerSimulations.SimulationProblemResults,
    expression::AbstractString;
    kwargs...
) -> Any

```

問題の各時間ステップに対して要求された式の最終値を返します。

ヘルプと例については[`read_realized_variable`](@ref)を参照してください。
