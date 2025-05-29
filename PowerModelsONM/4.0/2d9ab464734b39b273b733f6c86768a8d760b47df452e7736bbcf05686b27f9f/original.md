```
solve_robust_block_mld(
    data::Dict{String,<:Any},
    model_type::Type,
    solver,
    load_scenarios::Dict{Int, Dict{Any, Any}}
    kwargs...
)::Dict{String, Dict{String,Any}}
```

Solves a robust partitioning problem (mixed-integer) considering uncertainty using `model_type`, `solver`, and user-specified load uncertainty data `load_scenarios` (must be provided as allowed uncertainty range around base load value, which is the first scenario).
