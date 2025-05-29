```
run_fault_study(
    subnetwork::Dict{String,<:Any},
    faults::Dict{String,<:Any},
    solver
)::Dict{String,Any}
```

Uses `PowerModelsProtection.solve_mc_fault_study` to solve multiple faults defined in `faults`, applied to `subnetwork`, i.e., not a multinetwork, using a nonlinear `solver`.

Requires the use of `PowerModelsDistribution.IVRUPowerModel`.
