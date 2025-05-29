```
JSONRPCError(; id::Union{RequestId,Nothing}, error::ErrorInfo) <: Response
```

リクエストが失敗したときに返されるJSON-RPCエラー応答メッセージ。

# フィールド

  * `id::Union{RequestId,Nothing}`: この応答が対応するリクエストに一致する識別子、またはnull
  * `error::ErrorInfo`: 発生したエラーに関する情報
