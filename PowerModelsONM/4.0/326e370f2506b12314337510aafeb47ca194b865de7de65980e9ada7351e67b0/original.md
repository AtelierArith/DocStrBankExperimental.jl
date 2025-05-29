```
optimize_dispatch(
    network::Dict{String,<:Any},
    formulation::Type,
    solver;
    switching_solutions::Union{Missing,Dict{String,<:Any}}=missing
)::Dict{String,Any}
```

Solve a multinetwork optimal power flow (`solve_mn_mc_opf`) using `formulation` and `solver`
