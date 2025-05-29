```
answer!(
	answerer::SimpleAnswerer, index::AbstractDocumentIndex, result::AbstractRAGResult;
	model::AbstractString = PT.MODEL_CHAT, verbose::Bool = true,
	template::Symbol = :RAGAnswerFromContext,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...)
```

Generates an answer using the `aigenerate` function with the provided `result.context` and `result.question`.

# Returns

  * Mutated `result` with `result.answer` and the full conversation saved in `result.conversations[:answer]`

# Arguments

  * `answerer::SimpleAnswerer`: The method to use for generating the answer. Uses `aigenerate`.
  * `index::AbstractDocumentIndex`: The index containing chunks and sources.
  * `result::AbstractRAGResult`: The result containing the context and question to generate the answer for.
  * `model::AbstractString`: The model to use for generating the answer. Defaults to `PT.MODEL_CHAT`.
  * `verbose::Bool`: If `true`, enables verbose logging.
  * `template::Symbol`: The template to use for the `aigenerate` function. Defaults to `:RAGAnswerFromContext`.
  * `cost_tracker`: An atomic counter to track the cost of the operation.
