```
optimize_switches(
    subnetwork::Dict{String,<:Any},
    prob::Function,
    solver;
    formulation=PMD.LPUBFDiagPowerModel
)::Dict{String,Any}
```

Optimizes switch states for load shedding on a single subnetwork (not a multinetwork), using `prob`

Optionally, a PowerModelsDistribution `formulation` can be set independently, but is LinDist3Flow by default.
