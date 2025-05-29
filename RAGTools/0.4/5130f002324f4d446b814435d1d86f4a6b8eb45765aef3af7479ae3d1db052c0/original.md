```
refine!(
	refiner::SimpleRefiner, index::AbstractDocumentIndex, result::AbstractRAGResult;
	verbose::Bool = true,
	model::AbstractString = PT.MODEL_CHAT,
	template::Symbol = :RAGAnswerRefiner,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...)
```

Give model a chance to refine the answer (using the same or different context than previously provided).

This method uses the same context as the original answer, however, it can be modified to do additional retrieval and use a different context.

# Returns

  * Mutated `result` with `result.final_answer` and the full conversation saved in `result.conversations[:final_answer]`

# Arguments

  * `refiner::SimpleRefiner`: The method to use for refining the answer. Uses `aigenerate`.
  * `index::AbstractDocumentIndex`: The index containing chunks and sources.
  * `result::AbstractRAGResult`: The result containing the context and question to generate the answer for.
  * `model::AbstractString`: The model to use for generating the answer. Defaults to `PT.MODEL_CHAT`.
  * `verbose::Bool`: If `true`, enables verbose logging.
  * `template::Symbol`: The template to use for the `aigenerate` function. Defaults to `:RAGAnswerRefiner`.
  * `cost_tracker`: An atomic counter to track the cost of the operation.
