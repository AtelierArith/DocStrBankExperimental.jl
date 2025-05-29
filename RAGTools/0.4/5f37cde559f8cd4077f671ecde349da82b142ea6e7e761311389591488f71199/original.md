```
rephrase(rephraser::SimpleRephraser, question::AbstractString;
	verbose::Bool = true,
	model::String = PT.MODEL_CHAT, template::Symbol = :RAGQueryHyDE,
	cost_tracker = Threads.Atomic{Float64}(0.0))
```

Rephrases the `question` using the provided rephraser `template = RAGQueryHyDE`.

Special flavor of rephrasing using HyDE (Hypothetical Document Embedding) method,  which aims to find the documents most similar to a synthetic passage that *would be* a good answer to our question.

Returns both the original and the rephrased question.

# Arguments

  * `rephraser`: Type that dictates the logic of rephrasing step.
  * `question`: The question to be rephrased.
  * `model`: The model to use for rephrasing. Default is `PT.MODEL_CHAT`.
  * `template`: The rephrasing template to use. Default is `:RAGQueryHyDE`. Find more with `aitemplates("rephrase")`.
  * `verbose`: A boolean flag indicating whether to print verbose logging. Default is `true`.
