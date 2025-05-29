```
RAGResult
```

RAG回答のデバッグ用の構造体です。質問、回答、コンテキスト、およびRAGパイプラインの各ステップでの候補チャンクを含みます。

フローは `question` -> `rephrased_questions` -> `answer` -> `final_answer` と考えてください。コンテキストと候補チャンクがその過程を助けます。

# フィールド

  * `question::AbstractString`: 元の質問
  * `rephrased_questions::Vector{<:AbstractString}`: 言い換えられた質問のベクター（例: HyDe, Multihop など）
  * `answer::AbstractString`: 生成された回答
  * `final_answer::AbstractString`: 洗練された最終回答（例: CorrectiveRAGの後）

```
最終回答としても考慮されます（常に利用可能でなければなりません）
```

  * `context::Vector{<:AbstractString}`: 検索に使用されるコンテキスト（すなわち、ベクター

```
のチャンクとそれに関連するウィンドウが適用される場合）
```

  * `sources::Vector{<:AbstractString}`: コンテキストのソース（元の一致したチャンクのため）
  * `emb_candidates::CandidateChunks`: 埋め込みインデックスからの候補チャンク（`find_closest`から）
  * `tag_candidates::Union{Nothing, CandidateChunks}`: タグインデックスからの候補チャンク（`find_tags`から）
  * `filtered_candidates::CandidateChunks`: フィルタリングされた候補チャンク（

```
`emb_candidates` と `tag_candidates` の交差）
```

  * `reranked_candidates::CandidateChunks`: 再ランク付けされた候補チャンク（`rerank`から）
  * `conversations::Dict{Symbol,Vector{<:AbstractMessage}}`: RAGパイプラインのAIステップの会話履歴、

```
関数名に対応するキーを使用します。例: `:answer` または `:refine`
```

参照: `pprint`（整形出力）、`annotate_support`（回答の注釈用）
