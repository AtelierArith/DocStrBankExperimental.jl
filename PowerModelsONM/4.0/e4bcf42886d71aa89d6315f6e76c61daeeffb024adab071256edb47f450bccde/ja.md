```
build_settings_new(
    eng::Dict{String,<:Any};
    raw_settings::Dict{String,<:Any}=Dict{String,Any}(),
    switch_close_actions_ub::Union{Real}=missing,
    timestep_hours::Union{Missing,Real}=missing,
    vm_lb_pu::Union{Missing,Real}=missing,
    vm_ub_pu::Union{Missing,Real}=missing,
    vad_deg::Union{Missing,Real}=missing,
    line_limit_multiplier::Real=1.0,
    transformer_limit_multiplier::Real=1.0,
    generate_microgrid_ids::Bool=true,
    cold_load_pickup_factor::Union{Missing,Real}=missing,
    storage_phase_unbalance_factor::Union{Missing,Real}=missing,
)::Dict{String,Any}
```

`build_settings` 関数の新しいバージョンです。いくつかのフラグが `raw_settings` に移動されており、これは設定スキーマの形式に従う必要があります。
