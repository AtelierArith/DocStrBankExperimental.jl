```
optimize_dispatch(
    network::Dict{String,<:Any},
    formulation::Type,
    solver;
    switching_solutions::Union{Missing,Dict{String,<:Any}}=missing
)::Dict{String,Any}
```

`formulation` と `solver` を使用してマルチネットワーク最適電力フロー (`solve_mn_mc_opf`) を解決します。
