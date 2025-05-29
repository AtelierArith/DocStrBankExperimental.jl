```
annotate_support(
	annotater::TrigramAnnotater, result::AbstractRAGResult; min_score::Float64 = 0.5,
	skip_trigrams::Bool = true, hashed::Bool = true,
	min_source_score::Float64 = 0.25,
	add_sources::Bool = true,
	add_scores::Bool = true, kwargs...)
```

`AbstractRAGResult`型に対する`annotate_support`のディスパッチ。`result`から`final_answer`と`context`を抽出し、それらを使って`annotate_support`を呼び出します。

詳細については`annotate_support`を参照してください。

# 例

```julia
res = RAGResult(; question = "", final_answer = "This is a test.",
	context = ["Test context.", "Completely different"])
annotated_root = annotate_support(annotater, res)
PT.pprint(annotated_root)
```
