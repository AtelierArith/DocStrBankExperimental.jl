```
constraint_mc_transformer_power_block_on_off(pm::PMD.AbstractUnbalancedNFAModel, i::Int; nw::Int=nw_id_default, fix_taps::Bool=false)
```

transformer active power only constraint pf=-pt

$$
p_f[fc] == -pt[tc]
$$
