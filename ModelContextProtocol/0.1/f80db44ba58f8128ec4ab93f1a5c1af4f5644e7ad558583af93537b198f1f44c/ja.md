```
RequestContext(; server::Server, request_id::Union{RequestId,Nothing}=nothing, 
             progress_token::Union{ProgressToken,Nothing}=nothing)
```

MCPプロトコルハンドラのための現在のリクエストコンテキストを保存します。

# フィールド

  * `server::Server`: リクエストを処理するMCPサーバーインスタンス
  * `request_id::Union{RequestId,Nothing}`: 現在のリクエストのID（ある場合）
  * `progress_token::Union{ProgressToken,Nothing}`: 進捗報告のためのオプショナルトークン
