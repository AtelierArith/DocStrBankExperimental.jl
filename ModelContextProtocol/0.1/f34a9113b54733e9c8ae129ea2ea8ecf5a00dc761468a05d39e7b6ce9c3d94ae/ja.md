```
MCPResource(; uri, name::String, description::String="",
          mime_type::String="application/json", data_provider::Function,
          annotations::Dict{String,Any}=Dict{String,Any}()) <: Resource
```

MCPプロトコルでクライアントがアクセスできるリソースを実装します。リソースは、モデルやツールによって読み取ることができるデータを表します。

# フィールド

  * `uri::URI`: リソースの一意の識別子
  * `name::String`: リソースの人間が読める名前
  * `description::String`: リソースの詳細な説明
  * `mime_type::String`: リソースデータのMIMEタイプ
  * `data_provider::Function`: 呼び出されたときにリソースデータを提供する関数
  * `annotations::Dict{String,Any}`: リソースの追加メタデータ
