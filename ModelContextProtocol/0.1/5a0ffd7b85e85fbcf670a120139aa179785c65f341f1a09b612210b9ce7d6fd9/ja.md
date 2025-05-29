```
ErrorInfo(; code::Int, message::String, data::Union{Dict{String,Any},Nothing}=nothing)
```

JSON-RPCエラー応答のためのエラー情報構造体。

# フィールド

  * `code::Int`: 数値エラーコード（ErrorCodesモジュールで定義済み）
  * `message::String`: 人間が読めるエラーの説明
  * `data::Union{Dict{String,Any},Nothing}`: オプションの追加エラー詳細
