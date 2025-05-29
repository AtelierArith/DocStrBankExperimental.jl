```
MCPResource(; uri, name, description="", mime_type="application/json", 
          data_provider, annotations=Dict{String,Any}()) -> MCPResource
```

文字列からの自動URI変換を使用してリソースを作成します。

# 引数

  * `uri`: リソースのための文字列またはURI識別子
  * `name`: リソースのための人間が読める名前
  * `description`: 詳細な説明
  * `mime_type`: リソースのMIMEタイプ
  * `data_provider`: 呼び出されたときにリソースデータを返す関数
  * `annotations`: リソースのための追加メタデータ

# 戻り値

  * `MCPResource`: 提供された構成を持つ新しいリソース
