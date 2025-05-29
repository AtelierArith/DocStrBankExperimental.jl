```
EmbeddedResource(; resource::Union{TextResourceContents, BlobResourceContents}, 
                annotations::Dict{String,Any}=Dict{String,Any}()) <: Content
```

MCPスキーマで定義された埋め込みリソースコンテンツ。

# フィールド

  * `type::String`: コンテンツタイプ識別子（常に "resource"）
  * `resource::Union{TextResourceContents, BlobResourceContents}`: 埋め込みリソースコンテンツ
  * `annotations::Dict{String,Any}`: リソースに関するオプションのメタデータ
