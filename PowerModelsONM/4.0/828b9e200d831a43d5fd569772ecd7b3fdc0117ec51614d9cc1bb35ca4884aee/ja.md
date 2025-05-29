```
get_timestep_switch_optimization_metadata(
    optimal_switching_results::Dict{String,Any};
    opt_switch_algorithm::String="full-lookahead"
)::Vector{Dict{String,Any}}
```

各タイムステップの最適スイッチング結果からメタデータを取得し、`opt_switch_algorithm="iterative"`の場合は`Dict`のリストを、`opt_switch_algorithm="full-lookahead"`の場合は単一の`Dict`を含むリストを返します。
