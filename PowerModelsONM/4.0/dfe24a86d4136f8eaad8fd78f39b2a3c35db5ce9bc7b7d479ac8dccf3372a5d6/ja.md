```
get_timestep_bus_types!(args::Dict{String,<:Any})::Vector{Dict{String,String}}
```

最適な dispatch 結果から各タイムステップのバスタイプ（PQ、PV、ref、isolated）を取得し、それを `args["output_data"]["Protection settings"]["bus_types"]` に割り当てます。
