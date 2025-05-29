```julia
get_single_solution(
    res::HarmonicSteadyState.Result{D, S, P, F} where F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}};
    branch,
    index
)

```

Return an ordered dictionary specifying all variables and parameters of the solution in `result` on `branch` at the position `index`.
