```
find_closest(
	finder::AbstractSimilarityFinder, index::AbstractChunkIndex,
	query_emb::AbstractVector{<:Real}, query_tokens::AbstractVector{<:AbstractString} = String[];
	top_k::Int = 100, kwargs...)
```

Finds the indices of chunks (represented by embeddings in `index`) that are closest to query embedding (`query_emb`).

Returns only `top_k` closest indices.
