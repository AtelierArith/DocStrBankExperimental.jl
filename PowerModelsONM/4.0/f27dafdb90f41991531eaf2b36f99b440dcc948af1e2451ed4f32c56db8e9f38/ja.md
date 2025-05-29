```
get_timestep_dispatch!(
    args::Dict{String,<:Any}
)::Vector{Dict{String,Any}}
```

`args`に最適なディスパッチ結果をインプレースで取得し、[`entrypoint`](@ref entrypoint)で使用するために、[`get_timestep_dispatch`](@ref get_timestep_dispatch)を使用します。
