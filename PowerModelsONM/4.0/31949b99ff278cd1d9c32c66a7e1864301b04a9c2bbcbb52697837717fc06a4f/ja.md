```
get_timestep_dispatch(
    solution::Dict{String,<:Any},
    network::Dict{String,<:Any}
)::Vector{Dict{String,Any}}
```

最適な dispatch `solution` から各タイムステップの発電資産（発電機、ストレージ、太陽光、電圧源）およびバス電圧の大きさの SI 単位での dispatch 情報を返します。
