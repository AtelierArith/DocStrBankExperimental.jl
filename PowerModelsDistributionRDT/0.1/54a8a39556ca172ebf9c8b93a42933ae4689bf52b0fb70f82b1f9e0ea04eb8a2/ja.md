```
constraint_mc_ampacity_to_ne(pm::AbstractUnbalancedACPModel, nw::Int, t_idx::Tuple{Int,Int,Int}, t_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

neブランチのためのブランチのto側に対するACP電流制限制約

math`p_{to}^2 + q_{to}^2 \leq vm_{to}^2 i_{max}^2 * xe_s`
