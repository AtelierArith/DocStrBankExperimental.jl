```
rerank(
	reranker::RankGPTReranker, 
	index::AbstractDocumentIndex, 
	question::AbstractString,
	candidates::AbstractCandidateChunks;
	api_key::AbstractString = PT.OPENAI_API_KEY,
	model::AbstractString = PT.MODEL_CHAT,
	verbose::Bool = false,
	top_n::Integer = length(candidates.scores),
	unique_chunks::Bool = true,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...
)
```

Re-ranks a list of candidate chunks using the RankGPT algorithm. See https://github.com/sunnweiwei/RankGPT for more details. 

It uses LLM calls to rank the candidate chunks.

# Arguments

  * `reranker`: Using Cohere API
  * `index`: The index that holds the underlying chunks to be re-ranked.
  * `question`: The query to be used for the search.
  * `candidates`: The candidate chunks to be re-ranked.
  * `top_n`: The number of most relevant documents to return. Default is `length(documents)`.
  * `model`: The model to use for reranking. Default is `rerank-english-v3.0`.
  * `verbose`: A boolean flag indicating whether to print verbose logging. Default is `1`.
  * `unique_chunks`: A boolean flag indicating whether to remove duplicates from the candidate chunks prior to reranking (saves compute time). Default is `true`.

# Examples

```julia
index = <some index>
question = "What are the best practices for parallel computing in Julia?"

cfg = RAGConfig(; retriever = SimpleRetriever(; reranker = RT.RankGPTReranker()))
msg = airag(cfg, index; question, return_all = true)
```

To get full verbosity of logs, set `verbose = 5` (anything higher than 3).

```julia
msg = airag(cfg, index; question, return_all = true, verbose = 5)
```

# Reference

[1] [Is ChatGPT Good at Search? Investigating Large Language Models as Re-Ranking Agents by W. Sun et al.](https://arxiv.org/abs/2304.09542) [2] [RankGPT Github](https://github.com/sunnweiwei/RankGPT)
