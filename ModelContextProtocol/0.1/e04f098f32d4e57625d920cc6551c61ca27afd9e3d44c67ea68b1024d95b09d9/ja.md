```
ImageContent(; data::Vector{UInt8}, mime_type::String, annotations::Dict{String,Any}=Dict{String,Any}()) <: Content
```

MCPプロトコルメッセージのための画像ベースのコンテンツ。

# フィールド

  * `type::String`: コンテンツタイプ識別子（常に "image"）
  * `data::Vector{UInt8}`: バイナリ画像データ
  * `mime_type::String`: 画像のMIMEタイプ（例: "image/png"）
  * `annotations::Dict{String,Any}`: コンテンツに関するオプションのメタデータ
