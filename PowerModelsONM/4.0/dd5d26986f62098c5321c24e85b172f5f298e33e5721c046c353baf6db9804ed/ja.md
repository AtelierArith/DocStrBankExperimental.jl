```
get_timestep_voltage_statistics!(
    args::Dict{String,<:Any}
)::Dict{String,Vector{Real}}
```

引数の各タイムステップの電圧統計（最小、平均、最大）をインプレースで取得し、[`entrypoint`][@ref entrypoint]で使用するために、[`get_timestep_voltage_statistics`](@ref get_timestep_voltage_statistics)を使用します。
