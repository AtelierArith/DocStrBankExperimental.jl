```
rerank(
	reranker::CohereReranker, 
	index::AbstractDocumentIndex, 
	question::AbstractString,
	candidates::AbstractCandidateChunks;
	verbose::Bool = false,
	api_key::AbstractString = PT.COHERE_API_KEY,
	top_n::Integer = length(candidates.scores),
	model::AbstractString = "rerank-english-v3.0",
	return_documents::Bool = false,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...
)
```

Re-ranks a list of candidate chunks using the Cohere Rerank API. See https://cohere.com/rerank for more details. 

# Arguments

  * `reranker`: Using Cohere API
  * `index`: The index that holds the underlying chunks to be re-ranked.
  * `question`: The query to be used for the search.
  * `candidates`: The candidate chunks to be re-ranked.
  * `top_n`: The number of most relevant documents to return. Default is `length(documents)`.
  * `model`: The model to use for reranking. Default is `rerank-english-v3.0`.
  * `return_documents`: A boolean flag indicating whether to return the reranked documents in the response. Default is `false`.
  * `verbose`: A boolean flag indicating whether to print verbose logging. Default is `false`.
  * `cost_tracker`: An atomic counter to track the cost of the retrieval. Not implemented /tracked (cost unclear). Provided for consistency.
