```
rerank(
	reranker::CohereReranker, 
	index::AbstractDocumentIndex, 
	question::AbstractString,
	candidates::AbstractCandidateChunks;
	verbose::Bool = false,
	api_key::AbstractString = PT.COHERE_API_KEY,
	top_n::Integer = length(candidates.scores),
	model::AbstractString = "rerank-english-v3.0",
	return_documents::Bool = false,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...
)
```

Cohere Rerank APIを使用して候補チャンクのリストを再ランク付けします。詳細については https://cohere.com/rerank を参照してください。

# 引数

  * `reranker`: Cohere APIを使用
  * `index`: 再ランク付けされる基礎チャンクを保持するインデックス。
  * `question`: 検索に使用されるクエリ。
  * `candidates`: 再ランク付けされる候補チャンク。
  * `top_n`: 返す最も関連性の高いドキュメントの数。デフォルトは `length(documents)`。
  * `model`: 再ランク付けに使用するモデル。デフォルトは `rerank-english-v3.0`。
  * `return_documents`: レスポンスに再ランク付けされたドキュメントを返すかどうかを示すブールフラグ。デフォルトは `false`。
  * `verbose`: 詳細なログを出力するかどうかを示すブールフラグ。デフォルトは `false`。
  * `cost_tracker`: 取得のコストを追跡するためのアトミックカウンター。未実装/追跡されていない（コスト不明）。一貫性のために提供されています。
