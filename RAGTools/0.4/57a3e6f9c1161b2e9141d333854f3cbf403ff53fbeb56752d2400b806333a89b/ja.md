```
find_closest(
	finder::AbstractSimilarityFinder, index::AbstractChunkIndex,
	query_emb::AbstractVector{<:Real}, query_tokens::AbstractVector{<:AbstractString} = String[];
	top_k::Int = 100, kwargs...)
```

クエリ埋め込み（`query_emb`）に最も近いチャンク（`index`内の埋め込みで表される）のインデックスを見つけます。

最も近い`top_k`のインデックスのみを返します。
