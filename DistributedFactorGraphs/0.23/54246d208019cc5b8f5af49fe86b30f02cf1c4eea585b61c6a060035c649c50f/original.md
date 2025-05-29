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

List all the solvekeys used amongst all variables in the distributed factor graph object.

Related

[`listSupersolves`](@ref), [`getSolverDataDict`](@ref), [`listVariables`](@ref)
