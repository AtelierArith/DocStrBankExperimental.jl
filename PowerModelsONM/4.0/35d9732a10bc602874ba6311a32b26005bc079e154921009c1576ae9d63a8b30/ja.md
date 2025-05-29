```
get_timestep_device_actions!(args::Dict{String,<:Any})::Vector{Dict{String,Any}}
```

毎タイムステップでデバイスアクションを取得し、[`get_timestep_device_actions`](@ref get_timestep_device_actions)を使用してargsにインプレースで適用します。これは[`entrypoint`](@ref entrypoint)で使用されます。
