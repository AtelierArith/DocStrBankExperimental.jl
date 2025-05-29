```
InitializeParams(; capabilities::ClientCapabilities=ClientCapabilities(),
               clientInfo::Implementation=Implementation(),
               protocolVersion::String) <: RequestParams
```

MCPプロトコル初期化リクエストのためのパラメータ。

# フィールド

  * `capabilities::ClientCapabilities`: 報告されているクライアントの能力
  * `clientInfo::Implementation`: クライアント実装に関する情報
  * `protocolVersion::String`: 使用されているMCPプロトコルのバージョン
