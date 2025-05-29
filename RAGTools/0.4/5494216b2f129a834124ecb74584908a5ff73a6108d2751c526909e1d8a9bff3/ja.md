```
rerank(
	reranker::RankGPTReranker, 
	index::AbstractDocumentIndex, 
	question::AbstractString,
	candidates::AbstractCandidateChunks;
	api_key::AbstractString = PT.OPENAI_API_KEY,
	model::AbstractString = PT.MODEL_CHAT,
	verbose::Bool = false,
	top_n::Integer = length(candidates.scores),
	unique_chunks::Bool = true,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...
)
```

RankGPTアルゴリズムを使用して候補チャンクのリストを再ランク付けします。詳細については、https://github.com/sunnweiwei/RankGPT を参照してください。

LLM呼び出しを使用して候補チャンクをランク付けします。

# 引数

  * `reranker`: Cohere APIを使用
  * `index`: 再ランク付けされる基礎チャンクを保持するインデックス。
  * `question`: 検索に使用されるクエリ。
  * `candidates`: 再ランク付けされる候補チャンク。
  * `top_n`: 返す最も関連性の高いドキュメントの数。デフォルトは `length(documents)`。
  * `model`: 再ランク付けに使用するモデル。デフォルトは `rerank-english-v3.0`。
  * `verbose`: 詳細なログを出力するかどうかを示すブールフラグ。デフォルトは `1`。
  * `unique_chunks`: 再ランク付けの前に候補チャンクから重複を削除するかどうかを示すブールフラグ（計算時間を節約）。デフォルトは `true`。

# 例

```julia
index = <some index>
question = "Juliaにおける並列計算のベストプラクティスは何ですか？"

cfg = RAGConfig(; retriever = SimpleRetriever(; reranker = RT.RankGPTReranker()))
msg = airag(cfg, index; question, return_all = true)
```

ログの完全な詳細を取得するには、`verbose = 5`（3より大きい任意の値）に設定します。

```julia
msg = airag(cfg, index; question, return_all = true, verbose = 5)
```

# 参考文献

[1] [Is ChatGPT Good at Search? Investigating Large Language Models as Re-Ranking Agents by W. Sun et al.](https://arxiv.org/abs/2304.09542) [2] [RankGPT Github](https://github.com/sunnweiwei/RankGPT)
