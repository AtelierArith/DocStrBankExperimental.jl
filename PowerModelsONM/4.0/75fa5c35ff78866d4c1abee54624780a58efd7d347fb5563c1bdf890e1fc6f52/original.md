```
run_fault_studies!(
    args::Dict{String,<:Any};
    validate::Bool=true,
    solver::String="nlp_solver"
)::Dict{String,Any}
```

Runs fault studies using `args["faults"]`, if defined, and stores the results in-place in `args["fault_stuides_results"]`, for use in [`entrypoint`](@ref entrypoint), using [`run_fault_studies`](@ref run_fault_studies)
