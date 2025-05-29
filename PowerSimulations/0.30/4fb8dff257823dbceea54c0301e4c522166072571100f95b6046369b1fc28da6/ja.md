```julia
read_realized_dual(
    res::PowerSimulations.SimulationProblemResults,
    dual::AbstractString;
    kwargs...
) -> Any

```

問題の各時間ステップに対して要求された双対の最終値を返します。

ヘルプと例については[`read_realized_variable`](@ref)を参照してください。
