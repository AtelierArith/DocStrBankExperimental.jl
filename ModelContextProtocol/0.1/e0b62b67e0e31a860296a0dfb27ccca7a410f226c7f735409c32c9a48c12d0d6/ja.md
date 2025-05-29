```
ClientCapabilities(; experimental::Union{Dict{String,Dict{String,Any}},Nothing}=nothing,
                roots::Union{Dict{String,Bool},Nothing}=nothing,
                sampling::Union{Dict{String,Any},Nothing}=nothing)
```

MCPクライアントが初期化中に報告する機能。

# フィールド

  * `experimental::Union{Dict{String,Dict{String,Any}},Nothing}`: サポートされている実験的機能
  * `roots::Union{Dict{String,Bool},Nothing}`: クライアントがアクセスできるルートディレクトリ
  * `sampling::Union{Dict{String,Any},Nothing}`: モデル生成のためのサンプリング機能
