```
TextResourceContents(; uri::String, text::String, mime_type::Union{String,Nothing}=nothing) <: ResourceContents
```

MCPリソースのテキストベースの内容。

# フィールド

  * `uri::String`: リソースの一意の識別子
  * `text::String`: リソースのテキスト内容
  * `mime_type::Union{String,Nothing}`: コンテンツのオプションのMIMEタイプ
