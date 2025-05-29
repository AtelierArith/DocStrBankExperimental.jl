```
ListToolsResult(; tools::Vector{Dict{String,Any}}, 
              nextCursor::Union{String,Nothing}=nothing) <: ResponseResult
```

ツールリストリクエストから返された結果。

# フィールド

  * `tools::Vector{Dict{String,Any}}`: メタデータを持つ利用可能なツールのリスト
  * `nextCursor::Union{String,Nothing}`: 追加のツールを取得するためのオプションのページネーションカーソル
