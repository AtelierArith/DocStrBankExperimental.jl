```
run_stability_analysis!(
    args::Dict{String,<:Any};
    validate::Bool=true,
    formulation::Type=PMD.ACRUPowerModel,
    solver::String="nlp_solver"
)::Dict{String,Bool}
```

Runs small signal stability analysis using PowerModelsStability and determines if each timestep configuration is stable, in-place, storing the results in `args["stability_results"]`, for use in [`entrypoint`](@ref entrypoint), Uses [`run_stability_analysis`](@ref run_stability_analysis)

If `validate`, raw inverters data will be validated against JSON schema

The formulation can be specified with `formulation`, but note that it must result in `"vm"` and `"va"` variables in the solution, or else `PowerModelsDistribution.sol_data_model!` must support converting the voltage variables into polar coordinates.

`solver` (default: `"nlp_solver"`) specifies which solver in `args["solvers"]` to use for the stability analysis (NLP OPF)
