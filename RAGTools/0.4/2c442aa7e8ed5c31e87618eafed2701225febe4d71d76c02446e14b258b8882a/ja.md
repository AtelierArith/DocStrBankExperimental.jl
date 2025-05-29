```
find_closest(
	finder::CosineSimilarity, emb::AbstractMatrix{<:Real},
	query_emb::AbstractVector{<:Real}, query_tokens::AbstractVector{<:AbstractString} = String[];
	top_k::Int = 100, minimum_similarity::AbstractFloat = -1.0, kwargs...)
```

`emb`内の埋め込みで表されるチャンクのインデックスを、クエリ埋め込み（`query_emb`）に最も近い（`CosineSimilarity()`のコサイン類似度で）ものを見つけます。

`finder`は類似性検索に使用されるロジックです。デフォルトは`CosineSimilarity`です。

`minimum_similarity`が指定されている場合、それ以上の類似性を持つインデックスのみが返されます。類似性は-1から1の間であり（-1 = 完全に反対、1 = 完全に同じ）、

`top_k`の最も近いインデックスのみが返されます。
