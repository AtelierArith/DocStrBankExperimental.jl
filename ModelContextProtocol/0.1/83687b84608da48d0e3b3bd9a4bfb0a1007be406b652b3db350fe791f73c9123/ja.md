```
ListPromptsResult(; prompts::Vector{Dict{String,Any}}, 
                nextCursor::Union{String,Nothing}=nothing) <: ResponseResult
```

プロンプトリストリクエストから返される結果。

# フィールド

  * `prompts::Vector{Dict{String,Any}}`: メタデータを持つ利用可能なプロンプトのリスト
  * `nextCursor::Union{String,Nothing}`: 追加のプロンプトを取得するためのオプションのページネーションカーソル
