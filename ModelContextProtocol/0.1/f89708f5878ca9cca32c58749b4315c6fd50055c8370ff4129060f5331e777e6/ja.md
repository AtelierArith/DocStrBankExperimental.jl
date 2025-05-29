```
ListResourcesParams(; cursor::Union{String,Nothing}=nothing) <: RequestParams
```

MCPサーバーから利用可能なリソースのリストを要求するためのパラメータ。

# フィールド

  * `cursor::Union{String,Nothing}`: 長いリソースリストのためのオプションのページネーションカーソル
