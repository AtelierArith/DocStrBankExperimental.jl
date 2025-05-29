```
constraint_mc_ampacity_from_damaged(pm::AbstractUnbalancedACPModel, nw::Int, f_idx::Tuple{Int,Int,Int}, f_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

損傷した枝のためのブランチからのACP電流制限制約

math`p_{fr}^2 + q_{fr}^2 \leq vm_{fr}^2 i_{max}^2 *he_s`
