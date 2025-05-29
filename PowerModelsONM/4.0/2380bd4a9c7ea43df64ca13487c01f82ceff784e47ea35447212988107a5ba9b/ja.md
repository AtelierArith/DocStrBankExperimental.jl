```
parse_network!(args::Dict{String,<:Any})::Dict{String,Any}
```

[`parse_network`](@ref parse_network) のインプレースバージョンで、ENGINEERING マルチネットワークデータ構造を返します。これは `args` の `args["network"]` にあり、非展開の ENGINEERING データ構造を `args["base_network"]` に追加します。
