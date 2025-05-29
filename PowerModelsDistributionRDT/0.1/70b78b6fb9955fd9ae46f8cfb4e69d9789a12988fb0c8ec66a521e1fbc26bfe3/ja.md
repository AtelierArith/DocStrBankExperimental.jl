```
constraint_mc_switch_thermal_limit(pm::AbstractUnbalancedActivePowerModel, nw::Int, f_idx::Tuple{Int,Int,Int}, f_connections::Vector{Int}, rating::Vector{<:Real})::Nothing
```

アクティブパワーのみのスイッチ熱制限制約

math`-S_{max} \leq p_{fr} \leq S_{max}`
