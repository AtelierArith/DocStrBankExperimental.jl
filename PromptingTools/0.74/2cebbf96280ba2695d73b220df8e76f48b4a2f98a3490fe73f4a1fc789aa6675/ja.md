```
ToolMessage
```

ツール呼び出しのためのメッセージタイプです。

これは、リクエスト（フィールド `args`, `name`）とレスポンス（フィールド `content`）の両方を表します。

# フィールド

  * `content::Any`: メッセージの内容。
  * `req_id::Union{Nothing, Int}`: リクエストの一意のID。
  * `tool_call_id::String`: ツール呼び出しの一意のID。
  * `raw::AbstractString`: ツール呼び出しリクエストの生のJSON文字列。
  * `args::Union{Nothing, Dict{Symbol, Any}}`: ツール呼び出しリクエストの引数。
  * `name::Union{Nothing, String}`: ツール呼び出しリクエストの名前。
