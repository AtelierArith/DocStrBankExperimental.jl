```
MCPTool(; name::String, description::String, parameters::Vector{ToolParameter},
      handler::Function, return_type::Type{<:Content}=TextContent) <: Tool
```

クライアントがMCPプロトコルで呼び出すことができるツールを実装します。

# フィールド

  * `name::String`: ツールの一意の識別子
  * `description::String`: ツールの目的に関する人間が読める説明
  * `parameters::Vector{ToolParameter}`: ツールが受け入れるパラメータ
  * `handler::Function`: ツールの機能を実装する関数
  * `return_type::Type{<:Content}`: ハンドラの期待される戻り値の型

# ハンドラの戻り値の型

ツールハンドラは自動的に変換されるさまざまな型を返すことができます：

  * 指定されたContent型のインスタンス（TextContent、ImageContentなど）
  * Dict（自動的にJSONに変換され、TextContentにラップされる）
  * String（自動的にTextContentにラップされる）
  * Tuple{Vector{UInt8}, String}（自動的にImageContentにラップされる）
