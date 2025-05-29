```
solve_robust_block_mld(
    data::Dict{String,<:Any},
    model_type::Type,
    solver;
    N::Int, ΔL::Float64,
    kwargs...
)::Dict{String, Dict{String,Any}}
```

Solves a robust (N scenarios and ±ΔL load uncertainty) partitioning problem (mixed-integer) considering uncertainty using `model_type` and `solver`. The default number of scenarios is set to 2 with load uncertainty of ±10% (around base load) and scenratios are generated using generate*load*scenarios().
