```
answer!(
	answerer::SimpleAnswerer, index::AbstractDocumentIndex, result::AbstractRAGResult;
	model::AbstractString = PT.MODEL_CHAT, verbose::Bool = true,
	template::Symbol = :RAGAnswerFromContext,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...)
```

`result.context` と `result.question` を使用して `aigenerate` 関数を使って回答を生成します。

# 戻り値

  * `result.answer` と `result.conversations[:answer]` に保存された全会話を持つ変更された `result`

# 引数

  * `answerer::SimpleAnswerer`: 回答を生成するために使用するメソッド。`aigenerate` を使用します。
  * `index::AbstractDocumentIndex`: チャンクとソースを含むインデックス。
  * `result::AbstractRAGResult`: 回答を生成するためのコンテキストと質問を含む結果。
  * `model::AbstractString`: 回答を生成するために使用するモデル。デフォルトは `PT.MODEL_CHAT`。
  * `verbose::Bool`: `true` の場合、詳細なログを有効にします。
  * `template::Symbol`: `aigenerate` 関数に使用するテンプレート。デフォルトは `:RAGAnswerFromContext`。
  * `cost_tracker`: 操作のコストを追跡するための原子カウンター。
