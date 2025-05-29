```
constraint_mc_ampacity_from_ne(pm::AbstractUnbalancedACPModel, nw::Int, f_idx::Tuple{Int,Int,Int}, f_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

ACP current limit constraint on branches from-side for ne branches

math`p_{fr}^2 + q_{fr}^2 \leq vm_{fr}^2 i_{max}^2 *xe_s`
