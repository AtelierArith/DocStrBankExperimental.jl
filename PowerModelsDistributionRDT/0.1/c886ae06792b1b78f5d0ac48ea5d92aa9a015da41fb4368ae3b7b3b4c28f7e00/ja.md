```
constraint_mc_switch_inline_ne_ampacity(pm::AbstractUnbalancedRectangularModels, nw::Int, f_idx::Tuple{Int,Int,Int}, f_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

スイッチに関するACP電流制限制約

math`p_{fr}^2 + q_{fr}^2 \leq (vr_{fr}^2 + vi_{fr}^2) i_{max}^2`
