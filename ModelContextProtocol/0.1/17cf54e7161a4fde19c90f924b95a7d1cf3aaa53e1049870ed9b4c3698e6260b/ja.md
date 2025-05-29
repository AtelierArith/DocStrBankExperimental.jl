```
TextContent(; text::String, annotations::Dict{String,Any}=Dict{String,Any}()) <: Content
```

MCPプロトコルメッセージのためのテキストベースのコンテンツ。

# フィールド

  * `type::String`: コンテンツタイプ識別子（常に "text"）
  * `text::String`: 実際のテキストコンテンツ
  * `annotations::Dict{String,Any}`: コンテンツに関するオプションのメタデータ
