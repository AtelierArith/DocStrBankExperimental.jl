```julia
listSolveKeys(
    variable::DistributedFactorGraphs.DFGVariable
) -> Set{Symbol}
listSolveKeys(
    variable::DistributedFactorGraphs.DFGVariable,
    filterSolveKeys::Union{Nothing, Regex}
) -> Set{Symbol}
listSolveKeys(
    variable::DistributedFactorGraphs.DFGVariable,
    filterSolveKeys::Union{Nothing, Regex},
    skeys
) -> Any

```

分散因子グラフオブジェクト内のすべての変数で使用されるすべてのsolvekeysをリストします。

関連

[`listSupersolves`](@ref), [`getSolverDataDict`](@ref), [`listVariables`](@ref)
