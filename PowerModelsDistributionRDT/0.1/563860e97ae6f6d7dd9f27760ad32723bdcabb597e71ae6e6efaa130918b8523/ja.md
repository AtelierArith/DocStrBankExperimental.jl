```
constraint_mc_thermal_limit_to_damaged(pm::AbstractUnbalancedPowerModel, nw::Int, t_idx::Tuple{Int,Int,Int}, t_connections::Vector{Int}, rate_a::Vector{<:Real})::Nothing
```

損傷したブランチ（宛先側）に対する一般的な熱制限制約
