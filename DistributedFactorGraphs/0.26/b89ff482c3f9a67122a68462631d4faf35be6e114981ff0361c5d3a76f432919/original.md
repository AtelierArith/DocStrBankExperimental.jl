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

List all the solvekeys used amongst all variables in the distributed factor graph object.

Related

[`listSolveKeys`](@ref), [`getSolverDataDict`](@ref), [`listVariables`](@ref)
