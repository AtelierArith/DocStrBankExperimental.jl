```
run_stability_analysis(
    network::Dict{String,<:Any},
    inverters::Dict{String,<:Any},
    solver;
    formulation::Type=PMD.ACRUPowerModel,
    switching_solutions::Union{Missing,Dict{String,<:Any}}=missing,
    distributed::Bool=false
)::Dict{String,Bool}
```

Runs small signal stability analysis using PowerModelsStability and determines if each timestep configuration is stable

`inverters` is an already parsed inverters file using [`parse_inverters`](@ref parse_inverters)

The formulation can be specified with `formulation`, but note that it must result in `"vm"` and `"va"` variables in the solution, or else `PowerModelsDistribution.sol_data_model!` must support converting the voltage variables into polar coordinates.

`solver` for stability analysis (NLP OPF)
