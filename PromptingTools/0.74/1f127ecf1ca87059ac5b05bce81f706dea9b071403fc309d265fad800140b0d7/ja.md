```
AIToolRequest
```

AI生成ツールリクエストのメッセージタイプ。 `aitools` 関数によって返されます。

# フィールド

  * `content::Union{AbstractString, Nothing}`: メッセージの内容。
  * `tool_calls::Vector{ToolMessage}`: ツール呼び出しリクエストのベクター。
  * `name::Union{Nothing, String}`: 会話の中の `role` の名前。
  * `status::Union{Int, Nothing}`: APIからのメッセージのステータス。
  * `tokens::Tuple{Int, Int}`: 使用されたトークンの数（プロンプト、完了）。
  * `elapsed::Float64`: 応答を生成するのにかかった時間（秒）。
  * `cost::Union{Nothing, Float64}`: API呼び出しのコスト（`MODEL_REGISTRY`からの情報を使用して計算）。
  * `log_prob::Union{Nothing, Float64}`: 応答の対数確率。
  * `extras::Union{Nothing, Dict{Symbol, Any}}`: キーメッセージフィールドの一部ではない追加メタデータのための辞書。シリアライズ可能であるために、アイテムの数とシングルトンを制限するようにしてください。
  * `finish_reason::Union{Nothing, String}`: 応答が終了した理由。
  * `run_id::Union{Nothing, Int}`: 実行のユニークID。
  * `sample_id::Union{Nothing, Int}`: サンプルのユニークID（複数のサンプルが生成される場合、すべて同じ `run_id` を持ちます）。

ツール呼び出しリクエストのフィールドについては `ToolMessage` を参照してください。

参照: [`tool_calls`](@ref), [`execute_tool`](@ref), [`parse_tool`](@ref)
