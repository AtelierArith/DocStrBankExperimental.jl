```
get_timestep_switch_changes(
    network::Dict{String,<:Any},
    optimal_switching_results::Dict{String,<:Any}=Dict{String,Any}()
)::Vector{Vector{String}}
```

タイムステップ間で状態が変化したスイッチのリストを取得します（常に最初のタイムステップは空のリストであることを期待します）。これは、MLD問題からの解が`network`にマージされていることを期待します。
