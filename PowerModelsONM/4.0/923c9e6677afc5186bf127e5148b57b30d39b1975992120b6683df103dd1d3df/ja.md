```
get_timestep_voltage_statistics(
    solution::Dict{String,<:Any},
    network::Dict{String,<:Any};
    make_per_unit::Bool=true
)::Dict{String,Vector{Real}}
```

各タイムステップの最小、平均、最大電圧に関する統計を返します [`get_voltage_min_mean_max`](@ref get_voltage_min_mean_max)

`make_per_unit`（デフォルト: true）がtrueの場合、電圧統計はパーユニット表現で返されます。`make_per_unit`がfalseの場合、ネットワーク全体で異なる電圧基準があると、統計は意味を成しません。
