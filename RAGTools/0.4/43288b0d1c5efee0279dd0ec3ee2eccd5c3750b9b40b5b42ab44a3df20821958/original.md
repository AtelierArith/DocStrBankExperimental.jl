```
find_closest(
	finder::BM25Similarity, dtm::AbstractDocumentTermMatrix,
	query_emb::AbstractVector{<:Real}, query_tokens::AbstractVector{<:AbstractString} = String[];
	top_k::Int = 100, minimum_similarity::AbstractFloat = -1.0, kwargs...)
```

Finds the indices of chunks (represented by DocumentTermMatrix in `dtm`) that are closest to query tokens (`query_tokens`) using BM25.

Reference: [Wikipedia: BM25](https://en.wikipedia.org/wiki/Okapi_BM25). Implementation follows: [The Next Generation of Lucene Relevance](https://opensourceconnections.com/blog/2015/10/16/bm25-the-next-generation-of-lucene-relevation/).
