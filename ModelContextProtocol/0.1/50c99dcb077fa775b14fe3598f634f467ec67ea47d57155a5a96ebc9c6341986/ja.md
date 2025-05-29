```
CallToolResult(; content::Vector{Dict{String,Any}}, is_error::Bool=false) <: ResponseResult
```

ツール呼び出しから返された結果。

# フィールド

  * `content::Vector{Dict{String,Any}}`: ツールによって生成されたコンテンツ
  * `is_error::Bool`: ツールの実行がエラーを引き起こしたかどうか
