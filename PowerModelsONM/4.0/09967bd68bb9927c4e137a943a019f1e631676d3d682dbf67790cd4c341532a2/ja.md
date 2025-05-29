```
constraint_mc_transformer_power_yy_block_on_off(
    pm::PMD.LPUBFDiagModel,
    nw::Int,
    trans_id::Int,
    f_bus::Int,
    t_bus::Int,
    f_idx::Tuple{Int,Int,Int},
    t_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int},
    pol::Int,
    tm_set::Vector{<:Real},
    tm_fixed::Vector{Bool},
    tm_scale::Real
)
```

wye-wyeトランスの電力と電圧のリンク、tm_fixedがtrueであることを前提としています

$$
w_fr_i=(pol_i*tm_scale*tm_i)^2w_to_i
$$
