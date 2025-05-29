```julia
read_realized_aux_variable(
    res::PowerSimulations.SimulationProblemResults,
    aux_variable::AbstractString;
    kwargs...
) -> Any

```

問題の各時間ステップに対して要求された補助変数の最終値を返します。

ヘルプと例については[`read_realized_variable`](@ref)を参照してください。
