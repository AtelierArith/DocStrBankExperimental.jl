```
constraint_mc_ampacity_to(pm::AbstractUnbalancedACPModel, nw::Int, t_idx::Tuple{Int,Int,Int}, t_connections::Vector{Int}, c_rating::Vector{<:Real})::Nothing
```

ACP current limit constraint on branches to-side for damaged branches

math`p_{to}^2 + q_{to}^2 \leq vm_{to}^2 i_{max}^2 * he_s`
