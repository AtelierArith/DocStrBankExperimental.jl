```
find_closest(
	finder::BM25Similarity, dtm::AbstractDocumentTermMatrix,
	query_emb::AbstractVector{<:Real}, query_tokens::AbstractVector{<:AbstractString} = String[];
	top_k::Int = 100, minimum_similarity::AbstractFloat = -1.0, kwargs...)
```

BM25を使用して、クエリトークン（`query_tokens`）に最も近いチャンク（`dtm`内のDocumentTermMatrixで表される）のインデックスを見つけます。

参考文献: [Wikipedia: BM25](https://en.wikipedia.org/wiki/Okapi_BM25)。実装の詳細: [The Next Generation of Lucene Relevance](https://opensourceconnections.com/blog/2015/10/16/bm25-the-next-generation-of-lucene-relevation/)。
