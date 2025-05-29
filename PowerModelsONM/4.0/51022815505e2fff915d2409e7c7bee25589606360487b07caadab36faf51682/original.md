```
optimize_switches(
    network::Dict{String,<:Any},
    solver;
    formulation::Type=PMD.LPUBFDiagPowerModel,
    algorithm::String="full-lookahead"
)::Dict{String,Any}
```

  * `algorithm::String`, if `"rolling-horizon"`, iterates over all subnetworks in a multinetwork data structure `network`, in order, and solves the optimal switching / MLD problem sequentially, updating the next timestep with the new switch configurations and storage energies from the solved timestep. Otherwise, if `"full-lookahead"`, will solve all time steps in a single optimization problem (default: `"full-lookahead"`)
