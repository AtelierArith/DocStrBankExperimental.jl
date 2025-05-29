```
HandlerResult(; response::Union{Response,Nothing}=nothing, 
            error::Union{ErrorInfo,Nothing}=nothing)
```

リクエスト処理の結果を表します。

# フィールド

  * `response::Union{Response,Nothing}`: 送信するレスポンス（成功した場合）
  * `error::Union{ErrorInfo,Nothing}`: エラー情報（リクエストが失敗した場合）

HandlerResult は、レスポンスまたはエラーのいずれかを含む必要がありますが、両方を含むことはできません。
