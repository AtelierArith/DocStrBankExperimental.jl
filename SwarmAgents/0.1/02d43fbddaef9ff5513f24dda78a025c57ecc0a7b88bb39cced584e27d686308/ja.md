```
エージェント
```

エージェントは、LLM、ツール、および指示への参照を保持するステートレス構造体です。

# フィールド

  * `name::String`: エージェントの名前。
  * `model::String`: エージェントに使用するモデル。
  * `instructions::String`: エージェントの指示。
  * `tool_map::Dict{String, AbstractTool}`: エージェントが利用可能なツールの辞書。
  * `tool_choice::Union{String, Nothing}`: エージェントのツール選択。
  * `parallel_tool_calls::Bool`: 並列ツール呼び出しを許可するかどうか。デフォルトは `true` - まだサポートされていません。
