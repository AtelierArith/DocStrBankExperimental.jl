```
get_timestep_bus_types(
    optimal_dispatch_solution::Dict{String,<:Any},
    network::Dict{String,<:Any}
)::Vector{Dict{String,String}}
```

`optimal_dispatch_solution` から各タイムステップのバスタイプ（PQ、PV、ref、isolated）を取得します。
