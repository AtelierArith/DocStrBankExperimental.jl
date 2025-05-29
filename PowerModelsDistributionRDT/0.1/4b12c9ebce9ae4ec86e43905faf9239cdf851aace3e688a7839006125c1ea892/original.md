```
constraint_mc_ampacity_from_damaged(pm::AbstractUnbalancedRectangularModels, nw::Int, f_idx::Tuple{Int,Int,Int}, f_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

ACP current limit constraint on branches from-side on branches that are damaged

math`p_{fr}^2 + q_{fr}^2 \leq (vr_{fr}^2 + vi_{fr}^2) i_{max}^2 * he_s`
