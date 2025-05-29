```
ToolParameter(; name::String, description::String, type::String, required::Bool=false)
```

MCPツールのパラメータを定義します。

# フィールド

  * `name::String`: パラメータ名（params辞書のキーとして使用される）
  * `description::String`: パラメータの人間が読める説明
  * `type::String`: MCPスキーマで指定されたパラメータのタイプ（例："string"、"number"、"boolean"）
  * `required::Bool`: ツールの呼び出しにパラメータが必要かどうか
