```julia
read_realized_parameter(
    res::PowerSimulations.SimulationProblemResults,
    parameter::AbstractString;
    kwargs...
) -> Any

```

要求されたパラメータの最終値を問題の各時間ステップに対して返します。

ヘルプと例については[`read_realized_variable`](@ref)を参照してください。
