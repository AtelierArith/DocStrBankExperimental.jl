```
constraint_mc_ampacity_to_damaged(pm::AbstractUnbalancedRectangularModels, nw::Int, t_idx::Tuple{Int,Int,Int}, t_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

ACP current limit constraint on branches to-side that are damaged

math`p_{to}^2 + q_{to}^2 \leq (vr_{to}^2 + vi_{to}^2) i_{max}^2 * he_s`
