```
constraint_mc_ampacity_from_ne(pm::AbstractUnbalancedRectangularModels, nw::Int, f_idx::Tuple{Int,Int,Int}, f_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

ACP電流制限制約は、neであるブランチの側からブランチに適用されます。

math`p_{fr}^2 + q_{fr}^2 \leq (vr_{fr}^2 + vi_{fr}^2) i_{max}^2 * xe_s`
