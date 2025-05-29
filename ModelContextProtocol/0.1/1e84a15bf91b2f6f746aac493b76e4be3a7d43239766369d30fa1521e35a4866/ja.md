```
GetPromptParams(; name::String, arguments::Union{Dict{String,String},Nothing}=nothing) <: RequestParams
```

MCPサーバーから特定のプロンプトをリクエストするためのパラメータ。

# フィールド

  * `name::String`: 取得するプロンプトの名前
  * `arguments::Union{Dict{String,String},Nothing}`: プロンプトテンプレートに適用するオプションの引数
