```
constraint_mc_thermal_limit_to_damaged(pm::AbstractUnbalancedPowerModel, nw::Int, t_idx::Tuple{Int,Int,Int}, t_connections::Vector{Int}, rate_a::Vector{<:Real})::Nothing
```

ブランチ（到達側）の一般的な熱制限制約で、拡張に関するものです。
