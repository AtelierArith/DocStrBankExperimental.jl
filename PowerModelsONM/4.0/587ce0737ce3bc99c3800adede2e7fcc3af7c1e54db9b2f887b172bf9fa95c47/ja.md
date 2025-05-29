```
get_timestep_storage_soc!(
    args::Dict{String,<:Any}
)::Vector{Real}
```

`entrypoint`(@ref entrypoint)で使用するために、`get_timestep_storage_soc`(@ref get*timestep*storage_soc)を使用して、args内の各タイムステップの残りのストレージエネルギーのパーセンテージをインプレースで取得します。
