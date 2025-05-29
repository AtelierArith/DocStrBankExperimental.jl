```
ListToolsParams(; cursor::Union{String,Nothing}=nothing) <: RequestParams
```

MCPサーバーから利用可能なツールのリストをリクエストするためのパラメータ。

# フィールド

  * `cursor::Union{String,Nothing}`: 長いツールリストのためのオプションのページネーションカーソル
