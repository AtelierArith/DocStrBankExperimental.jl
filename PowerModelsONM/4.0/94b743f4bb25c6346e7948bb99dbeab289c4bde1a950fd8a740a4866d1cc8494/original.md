```
run_fault_studies(
    network::Dict{String,<:Any},
    solver;
    faults::Dict{String,<:Any}=Dict{String,Any}(),
    switching_solutions::Union{Missing,Dict{String,<:Any}}=missing,
    dispatch_solution::Union{Missing,Dict{String,<:Any}}=missing,
    distributed::Bool=false
)::Dict{String,Any}
```

Runs fault studies defined in ieee13*faults.json. If no faults file is provided, it will automatically generate faults using `PowerModelsProtection.build*mc*fault*study`.

It will convert storage to limited generators, since storage is not yet supported in IVRU models in PowerModelsProtection

Uses [`run_fault_study`](@ref run_fault_study) to solve the actual fault study.

`solver` will determine which instantiated solver is used, `"nlp_solver"` or `"juniper_solver"`
