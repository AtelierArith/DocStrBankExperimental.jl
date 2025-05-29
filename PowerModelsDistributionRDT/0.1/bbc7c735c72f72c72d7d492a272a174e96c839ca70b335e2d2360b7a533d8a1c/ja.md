```
constraint_mc_ampacity_to_damaged(pm::AbstractUnbalancedRectangularModels, nw::Int, t_idx::Tuple{Int,Int,Int}, t_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

損傷を受けた側の枝に対するACP電流制限制約

math`p_{to}^2 + q_{to}^2 \leq (vr_{to}^2 + vi_{to}^2) i_{max}^2 * he_s`
