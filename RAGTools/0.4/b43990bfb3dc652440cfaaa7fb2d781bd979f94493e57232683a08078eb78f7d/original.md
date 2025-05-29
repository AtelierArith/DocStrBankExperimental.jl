```
run_qa_evals(index::AbstractChunkIndex, qa_items::AbstractVector{<:QAEvalItem};
	api_kwargs::NamedTuple = NamedTuple(),
	airag_kwargs::NamedTuple = NamedTuple(),
	qa_evals_kwargs::NamedTuple = NamedTuple(),
	verbose::Bool = true, parameters_dict::Dict{Symbol, <:Any} = Dict{Symbol, Any}())
```

Evaluates a vector of `QAEvalItem`s and returns a vector `QAEvalResult`.  This function assesses the relevance and accuracy of the answers generated in a QA evaluation context.

See `?run_qa_evals` for more details.

# Arguments

  * `qa_items::AbstractVector{<:QAEvalItem}`: The vector of QA evaluation items containing the questions and their answers.
  * `verbose::Bool`: If `true`, enables verbose logging. Defaults to `true`.
  * `api_kwargs::NamedTuple`: Parameters that will be forwarded to the API calls. See `?aiextract` for details.
  * `airag_kwargs::NamedTuple`: Parameters that will be forwarded to `airag` calls. See `?airag` for details.
  * `qa_evals_kwargs::NamedTuple`: Parameters that will be forwarded to `run_qa_evals` calls. See `?run_qa_evals` for details.
  * `parameters_dict::Dict{Symbol, Any}`: Track any parameters used for later evaluations. Keys must be Symbols.

# Returns

`Vector{QAEvalResult}`: Vector of evaluation results that includes various scores and metadata related to the QA evaluation.

# Example

```julia
index = "..." # Assuming a proper index is defined
qa_items = [QAEvalItem(question="What is the capital of France?", answer="Paris", context="France is a country in Europe."),
			QAEvalItem(question="What is the capital of Germany?", answer="Berlin", context="Germany is a country in Europe.")]

# Let's run a test with `top_k=5`
results = run_qa_evals(index, qa_items; airag_kwargs=(;top_k=5), parameters_dict=Dict(:top_k => 5))

# Filter out the "failed" calls
results = filter(x->!isnothing(x.answer_score), results);

# See average judge score
mean(x->x.answer_score, results)
```
