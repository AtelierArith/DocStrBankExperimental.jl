```
solve_mc_fault_study(case::Dict{String,<:Any}, fault_studies::Dict{String,<:Any}, solver; kwargs...)
```

Solves a series of fault studies given by `fault_studies`, e.g., built from [`build_mc_fault_study`](@ref build_mc_fault_study).
