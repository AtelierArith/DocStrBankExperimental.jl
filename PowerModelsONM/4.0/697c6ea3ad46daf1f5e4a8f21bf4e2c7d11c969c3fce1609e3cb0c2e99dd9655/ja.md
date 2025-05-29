```
get_timestep_fault_currents!(
    args::Dict{String,<:Any}
)::Vector{Dict{String,Any}}
```

引数の中で研究からのスイッチの故障電流と対応する故障を取得します。これは [`entrypoint`](@ref entrypoint) で使用するためであり、[`get_timestep_fault_currents`](@ref get_timestep_fault_currents) を使用します。
