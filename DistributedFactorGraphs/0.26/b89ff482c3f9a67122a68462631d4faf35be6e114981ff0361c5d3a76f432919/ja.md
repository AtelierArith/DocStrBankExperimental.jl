```julia
listSolveKeys(
    variable::DistributedFactorGraphs.VariableCompute
) -> Set{Symbol}
listSolveKeys(
    variable::DistributedFactorGraphs.VariableCompute,
    filterSolveKeys::Union{Nothing, Regex}
) -> Set{Symbol}
listSolveKeys(
    variable::DistributedFactorGraphs.VariableCompute,
    filterSolveKeys::Union{Nothing, Regex},
    skeys
) -> Any

```

分散ファクターグラフオブジェクト内のすべての変数で使用されるすべてのsolvekeysをリストします。

関連

[`listSolveKeys`](@ref), [`getSolverDataDict`](@ref), [`listVariables`](@ref)
