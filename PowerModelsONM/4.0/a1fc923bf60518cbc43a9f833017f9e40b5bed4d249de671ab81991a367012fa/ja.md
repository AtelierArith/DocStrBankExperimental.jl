```
constraint_mc_transformer_power_yy_traditional_on_off(pm::PMD.LPUBFDiagModel, nw::Int, trans_id::Int, f_bus::Int, t_bus::Int, f_idx::Tuple{Int,Int,Int}, t_idx::Tuple{Int,Int,Int}, f_connections::Vector{Int}, t_connections::Vector{Int}, pol::Int, tm_set::Vector{<:Real}, tm_fixed::Vector{Bool}, tm_scale::Real)

リンクは、wye-wye変圧器の電力と電圧の間にあり、tm_fixedがtrueであると仮定します
```

$$
w_fr_i=(pol_i*tm_scale*tm_i)^2w_to_i
$$
