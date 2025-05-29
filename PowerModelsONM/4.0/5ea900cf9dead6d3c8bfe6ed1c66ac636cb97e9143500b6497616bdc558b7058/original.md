```
optimize_dispatch!(
    args::Dict{String,<:Any};
    solver::Union{Missing,String}=missing
)::Dict{String,Any}
```

Solves optimal dispatch problem in-place, for use in [`entrypoint`](@ref entrypoint), using [`optimize_dispatch`](@ref optimize_dispatch). If you are using this to optimize after running [`optimize_switches!`](@ref optimize_switches!), this assumes that the correct switch states from those results have already been propagated into `args["network"]`

`solver` (default: `"nlp_solver"`) specifies which solver to use for the OPF problem from `args["solvers"]`
