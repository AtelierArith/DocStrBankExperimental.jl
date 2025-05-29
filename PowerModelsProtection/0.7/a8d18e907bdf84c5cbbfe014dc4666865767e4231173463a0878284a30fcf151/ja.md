```
solve_mc_fault_study(case::Dict{String,<:Any}, fault_studies::Dict{String,<:Any}, solver; kwargs...)
```

`fault_studies`によって与えられた一連の故障研究を解決します。例えば、[`build_mc_fault_study`](@ref build_mc_fault_study)から構築されたものです。
