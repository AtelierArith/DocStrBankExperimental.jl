```
convert_deprecated_runtime_args!(
    runtime_args::Dict{String,<:Any},
    settings::Dict{String,<:Any},
    base_network::Dict{String,<:Any},
    timesteps::Int
)::Tuple{Dict{String,Any},Dict{String,Any}}
```

非推奨のランタイム引数を適切なネットワーク設定構造に変換するためのヘルパー関数
