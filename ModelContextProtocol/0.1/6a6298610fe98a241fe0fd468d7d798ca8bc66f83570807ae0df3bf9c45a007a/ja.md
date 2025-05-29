```
ListPromptsParams(; cursor::Union{String,Nothing}=nothing) <: RequestParams
```

MCPサーバーから利用可能なプロンプトのリストを要求するためのパラメータ。

# フィールド

  * `cursor::Union{String,Nothing}`: 長いプロンプトリストのためのオプションのページネーションカーソル
