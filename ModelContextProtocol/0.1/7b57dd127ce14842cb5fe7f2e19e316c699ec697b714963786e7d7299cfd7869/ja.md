```
CallToolParams(; name::String, arguments::Union{Dict{String,Any},Nothing}=nothing) <: RequestParams
```

MCPサーバー上で特定のツールを呼び出すためのパラメータ。

# フィールド

  * `name::String`: 呼び出すツールの名前
  * `arguments::Union{Dict{String,Any},Nothing}`: ツールに渡すオプションの引数
