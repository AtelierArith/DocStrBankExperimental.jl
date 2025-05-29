```
constraint_mc_switch_inline_ne_ampacity(pm::AbstractUnbalancedWModels, nw::Int, f_idx::Tuple{Int,Int,Int}, f_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

ACP current limit constraint on switches from-side

math`p_{fr}^2 + q_{fr}^2 \leq w_{fr} i_{max}^2`
