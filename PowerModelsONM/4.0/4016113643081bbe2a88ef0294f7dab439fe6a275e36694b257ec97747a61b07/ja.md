```
check_switch_state_feasibility(data::Dict{String,<:Any})::Union{Dict{String,Bool},Bool}
```

ユーザーがネットワークモデルに実行可能な初期スイッチ構成があるかどうかを判断するのを助けるヘルパー関数（ネットワークモデルがマルチネットワークである場合、各タイムステップで、放射制約が適用されると仮定）。
