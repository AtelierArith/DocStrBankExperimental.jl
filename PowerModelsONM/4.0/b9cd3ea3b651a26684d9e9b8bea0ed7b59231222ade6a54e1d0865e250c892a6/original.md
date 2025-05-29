```
run_stability_analysis(
    subnetwork::Dict{String,<:Any},
    omega0::Real,
    rN::Int,
    solver;
    formulation::Type=PMD.ACPUPowerModel
)::Bool
```

Runs stability analysis on a single subnetwork (not a multinetwork) using a nonlinear `solver`.
