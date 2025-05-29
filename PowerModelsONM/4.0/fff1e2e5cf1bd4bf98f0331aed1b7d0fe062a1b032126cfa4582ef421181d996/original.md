```
optimize_switches!(args::Dict{String,<:Any})::Dict{String,Any}
```

Optimizes switch states (therefore shedding load or not) in-place, for use in [`entrypoint`](@ref entrypoint), using [`optimize_switches`]

Uses LPUBFDiagPowerModel (LinDist3Flow), and therefore requires `args["solvers"]["misocp_solver"]` to be specified
