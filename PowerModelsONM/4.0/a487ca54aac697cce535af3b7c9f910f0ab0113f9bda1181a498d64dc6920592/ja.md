```
get_timestep_device_actions(
    network::Dict{String,<:Any},
    optimal_switching_results::Dict{String,<:Any}
)::Vector{Dict{String,Any}}
```

マルチネットワーク `network` から、各タイムステップでのスイッチ構成を決定します。スイッチが `mld_results` に存在しない場合、状態は元のネットワークで与えられた状態にデフォルトで戻ります。これは、スイッチがディスパッチ可能でない場合に発生する可能性があり、そのため `state` は結果に期待されないでしょう。

出力は Vector{Dict} であり、各 Dict には `"Switch configurations"` が含まれ、これはスイッチ名をキーとし、スイッチの状態である `"open"` または `"closed"` を値とする Dict です。また、`"Shedded loads"` には、そのタイムステップでシェッドされた負荷名のリストが含まれます。
