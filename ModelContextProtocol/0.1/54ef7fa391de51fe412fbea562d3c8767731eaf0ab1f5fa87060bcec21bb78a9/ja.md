```
InitializeResult(; serverInfo::Dict{String,Any}, capabilities::Dict{String,Any},
               protocolVersion::String, instructions::String="") <: ResponseResult
```

MCPプロトコル初期化に対する応答として返される結果。

# フィールド

  * `serverInfo::Dict{String,Any}`: サーバー実装に関する情報
  * `capabilities::Dict{String,Any}`: 報告されているサーバーの機能
  * `protocolVersion::String`: 使用されているMCPプロトコルのバージョン
  * `instructions::String`: クライアント向けのオプションの使用指示
