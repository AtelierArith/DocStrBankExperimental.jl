```
find_closest(
	finder::CosineSimilarity, emb::AbstractMatrix{<:Real},
	query_emb::AbstractVector{<:Real}, query_tokens::AbstractVector{<:AbstractString} = String[];
	top_k::Int = 100, minimum_similarity::AbstractFloat = -1.0, kwargs...)
```

Finds the indices of chunks (represented by embeddings in `emb`) that are closest (in cosine similarity for `CosineSimilarity()`) to query embedding (`query_emb`). 

`finder` is the logic used for the similarity search. Default is `CosineSimilarity`.

If `minimum_similarity` is provided, only indices with similarity greater than or equal to it are returned.  Similarity can be between -1 and 1 (-1 = completely opposite, 1 = exactly the same).

Returns only `top_k` closest indices.
