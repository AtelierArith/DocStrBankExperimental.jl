```
get_timestep_stability!(
    args::Dict{String,<:Any}
)::Vector{Bool}
```

各タイムステップでの安定性を取得し、[`entrypoint`](@ref entrypoint)で使用するために、[`get_timestep_stability`](@ref get_timestep_stability)を使用してargsにインプレースで適用します。
