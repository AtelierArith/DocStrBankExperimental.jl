```
apply_switch_solutions!(network::Dict{String,<:Any}, optimal_switching_results::Dict{String,<:Any})::Dict{String,Any}
```

最適なスイッチング結果 `optimal_switching_results` からの結果で、マルチネットワーク `network` をインプレースで更新します。

[`optimize_switches!`](@ref optimize_switches!) のインプレースバージョンを使用しない場合に使用されます。
