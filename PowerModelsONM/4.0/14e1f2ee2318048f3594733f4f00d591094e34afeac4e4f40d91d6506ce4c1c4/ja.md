```
get_timestep_fault_study_metadata(
    fault_studies_results::Dict{String,Any}
)::Vector{Dict{String,Any}}
```

各タイムステップの最適スイッチング結果からメタデータを取得し、Dictのリストを返します（`opt_switch_algorithm="rolling-horizon"`の場合）、または単一のDictを含むリストを返します（`opt_switch_algorithm="full-lookahead"`の場合）。
