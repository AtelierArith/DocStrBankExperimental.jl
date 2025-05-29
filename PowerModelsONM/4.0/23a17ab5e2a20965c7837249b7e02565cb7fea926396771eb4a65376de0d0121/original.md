```
generate_load_scenarios(data::Dict{String,<:Any}, N::Int, ΔL::Float64)::Dict{Int,Dict{Any,Any}}
```

Generate N scenarios with ±ΔL uncertainty around base load. The first scenario always uses base load. PMD.solve*mc*opf() is solved for each scenario to check if feasible to original problem (`data` is network with no microgrids, all blocks energized by substation)
