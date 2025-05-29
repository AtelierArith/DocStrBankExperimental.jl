```
ResourceTemplate(; name::String, uri_template::String,
               mime_type::Union{String,Nothing}=nothing, description::String="")
```

パラメータ化されたURIを使用してリソースを動的に生成するためのテンプレートを定義します。

# フィールド

  * `name::String`: リソーステンプレートの名前
  * `uri_template::String`: パラメータのプレースホルダーを含むテンプレート文字列
  * `mime_type::Union{String,Nothing}`: 生成されるリソースのMIMEタイプ
  * `description::String`: テンプレートの人間が読める説明
