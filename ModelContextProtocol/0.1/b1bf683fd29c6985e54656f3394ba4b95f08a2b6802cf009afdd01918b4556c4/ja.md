```
BlobResourceContents(; uri::String, blob::Vector{UInt8}, mime_type::Union{String,Nothing}=nothing) <: ResourceContents
```

MCPリソースのバイナリコンテンツ。

# フィールド

  * `uri::String`: リソースの一意の識別子
  * `blob::Vector{UInt8}`: リソースのバイナリコンテンツ
  * `mime_type::Union{String,Nothing}`: コンテンツのオプションのMIMEタイプ
