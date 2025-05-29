```
ChunkKeywordsIndex(
	[processor::AbstractProcessor=KeywordsProcessor(),] index::ChunkEmbeddingsIndex; verbose::Int = 1,
	index_id = gensym("ChunkKeywordsIndex"), processor_kwargs...)
```

Convenience method to quickly create a `ChunkKeywordsIndex` from an existing `ChunkEmbeddingsIndex`.

# Example

```julia

# Let's assume we have a standard embeddings-based index
index = build_index(SimpleIndexer(), texts; chunker_kwargs = (; max_length=10))

# Creating an additional index for keyword-based search (BM25), is as simple as
index_keywords = ChunkKeywordsIndex(index)

# We can immediately create a MultiIndex (a hybrid index holding both indices)
multi_index = MultiIndex([index, index_keywords])

```
