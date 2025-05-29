```
get_timestep_dispatch_optimization_metadata(
    optimal_dispatch_result::Dict{String,Any}
)::Dict{String,Any}
```

各タイムステップの最適スイッチング結果からメタデータを取得し、`opt_switch_algorithm="rolling-horizon"`の場合はDictのリストを、`opt_switch_algorithm="full-lookahead"`の場合は単一のDictを含むリストを返します。
