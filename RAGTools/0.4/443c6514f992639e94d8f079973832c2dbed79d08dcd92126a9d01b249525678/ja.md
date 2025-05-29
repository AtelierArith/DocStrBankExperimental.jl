```
ChunkKeywordsIndex(
	[processor::AbstractProcessor=KeywordsProcessor(),] index::ChunkEmbeddingsIndex; verbose::Int = 1,
	index_id = gensym("ChunkKeywordsIndex"), processor_kwargs...)
```

既存の `ChunkEmbeddingsIndex` から `ChunkKeywordsIndex` を迅速に作成するための便利なメソッドです。

# 例

```julia

# 標準の埋め込みベースのインデックスがあると仮定しましょう
index = build_index(SimpleIndexer(), texts; chunker_kwargs = (; max_length=10))

# キーワードベースの検索（BM25）のための追加インデックスを作成するのは簡単です
index_keywords = ChunkKeywordsIndex(index)

# すぐに両方のインデックスを保持するハイブリッドインデックスである MultiIndex を作成できます
multi_index = MultiIndex([index, index_keywords])

```
