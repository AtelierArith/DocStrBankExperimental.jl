```
annotate_support(
	annotater::TrigramAnnotater, result::AbstractRAGResult; min_score::Float64 = 0.5,
	skip_trigrams::Bool = true, hashed::Bool = true,
	min_source_score::Float64 = 0.25,
	add_sources::Bool = true,
	add_scores::Bool = true, kwargs...)
```

Dispatch for `annotate_support` for `AbstractRAGResult` type. It extracts the `final_answer` and `context` from the `result` and calls `annotate_support` with them.

See `annotate_support` for more details.

# Example

```julia
res = RAGResult(; question = "", final_answer = "This is a test.",
	context = ["Test context.", "Completely different"])
annotated_root = annotate_support(annotater, res)
PT.pprint(annotated_root)
```
