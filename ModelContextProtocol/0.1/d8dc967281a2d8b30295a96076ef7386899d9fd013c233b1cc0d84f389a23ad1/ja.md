```
ListResourcesResult(; resources::Vector{Dict{String,Any}}, 
                  nextCursor::Union{String,Nothing}=nothing) <: ResponseResult
```

リストリソースリクエストから返される結果。

# フィールド

  * `resources::Vector{Dict{String,Any}}`: メタデータを持つ利用可能なリソースのリスト
  * `nextCursor::Union{String,Nothing}`: 追加のリソースを取得するためのオプションのページネーションカーソル
