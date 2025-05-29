```
get_timestep_switch_optimization_metadata!(
    args::Dict{String,<:Any}
)::Vector{Dict{String,Any}}
```

最適なスイッチングソリューションからスイッチング最適化結果のメタデータを[`get_timestep_switch_optimization_metadata`](@ref get_timestep_switch_optimization_metadata)を介して取得し、それをargsにインプレースで適用して、[`entrypoint`](@ref entrypoint)で使用します。
