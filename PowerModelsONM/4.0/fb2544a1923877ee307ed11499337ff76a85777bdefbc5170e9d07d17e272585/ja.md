```
get_timestep_generator_profiles!(
    args::Dict{String,<:Any}
)::Dict{String,Vector{Real}}
```

引数の各タイムステップの発電機プロファイル統計を、[`entrypoint`](@ref entrypoint)で使用するために、`args`内でインプレースで取得します。[`get_timestep_generator_profiles`](@ref get_timestep_generator_profiles)を使用します。
