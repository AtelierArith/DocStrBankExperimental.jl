```
constraint_mc_ampacity_to_ne(pm::AbstractUnbalancedWModels, nw::Int, t_idx::Tuple{Int,Int,Int}, t_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

ACP電流制限制約は、ned math`p_{to}^2 + q_{to}^2 \leq w_{to} i_{max}^2 # xe_s`に対して、ブランチのto側に適用されます。
