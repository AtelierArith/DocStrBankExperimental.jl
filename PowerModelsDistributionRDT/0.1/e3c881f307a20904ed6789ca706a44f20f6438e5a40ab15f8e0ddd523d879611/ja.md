```
constraint_mc_ampacity_from_ne(pm::AbstractUnbalancedWModels, nw::Int, f_idx::Tuple{Int,Int,Int}, f_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

枝のneからのACP電流制限制約

math`p_{fr}^2 + q_{fr}^2 \leq w_{fr} i_{max}^2 * xe_s`
