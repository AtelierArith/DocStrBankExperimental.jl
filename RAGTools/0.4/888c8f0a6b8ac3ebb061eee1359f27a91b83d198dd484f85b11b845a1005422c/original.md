```
refine!(
	refiner::TavilySearchRefiner, index::AbstractDocumentIndex, result::AbstractRAGResult;
	verbose::Bool = true,
	model::AbstractString = PT.MODEL_CHAT,
	include_answer::Bool = true,
	max_results::Integer = 5,
	include_domains::AbstractVector{<:AbstractString} = String[],
	exclude_domains::AbstractVector{<:AbstractString} = String[],
	template::Symbol = :RAGWebSearchRefiner,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...)
```

Refines the answer by executing a web search using the Tavily API. This method aims to enhance the answer's accuracy and relevance by incorporating information retrieved from the web.

Note: The web results and web answer (if requested) will be added to the context and sources!

# Returns

  * Mutated `result` with `result.final_answer` and the full conversation saved in `result.conversations[:final_answer]`.
  * In addition, the web results and web answer (if requested) are appended to the `result.context` and `result.sources` for correct highlighting and verification.

# Arguments

  * `refiner::TavilySearchRefiner`: The method to use for refining the answer. Uses `aigenerate` with a web search template.
  * `index::AbstractDocumentIndex`: The index containing chunks and sources.
  * `result::AbstractRAGResult`: The result containing the context and question to generate the answer for.
  * `model::AbstractString`: The model to use for generating the answer. Defaults to `PT.MODEL_CHAT`.
  * `include_answer::Bool`: If `true`, includes the answer from Tavily in the web search.
  * `max_results::Integer`: The maximum number of results to return.
  * `include_domains::AbstractVector{<:AbstractString}`: A list of domains to include in the search results. Default is an empty list.
  * `exclude_domains::AbstractVector{<:AbstractString}`: A list of domains to exclude from the search results. Default is an empty list.
  * `verbose::Bool`: If `true`, enables verbose logging.
  * `template::Symbol`: The template to use for the `aigenerate` function. Defaults to `:RAGWebSearchRefiner`.
  * `cost_tracker`: An atomic counter to track the cost of the operation.

# Example

```julia
refiner!(TavilySearchRefiner(), index, result)
# See result.final_answer or pprint(result)
```

To enable this refiner in a full RAG pipeline, simply swap the component in the config:

```julia
cfg = RT.RAGConfig()
cfg.generator.refiner = RT.TavilySearchRefiner()

result = airag(cfg, index; question, return_all = true)
pprint(result)
```
