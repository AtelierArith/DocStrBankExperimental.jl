```
build_qa_evals(doc_chunks::Vector{<:AbstractString}, sources::Vector{<:AbstractString};
			   model=PT.MODEL_CHAT, instructions="None.", qa_template::Symbol=:RAGCreateQAFromContext, 
			   verbose::Bool=true, api_kwargs::NamedTuple = NamedTuple(), kwargs...) -> Vector{QAEvalItem}
```

Create a collection of question and answer evaluations (`QAEvalItem`) from document chunks and sources.  This function generates Q&A pairs based on the provided document chunks, using a specified AI model and template.

# Arguments

  * `doc_chunks::Vector{<:AbstractString}`: A vector of document chunks, each representing a segment of text.
  * `sources::Vector{<:AbstractString}`: A vector of source identifiers corresponding to each chunk in `doc_chunks` (eg, filenames or paths).
  * `model`: The AI model used for generating Q&A pairs. Default is `PT.MODEL_CHAT`.
  * `instructions::String`: Additional instructions or context to provide to the model generating QA sets. Defaults to "None.".
  * `qa_template::Symbol`: A template symbol that dictates the AITemplate that will be used. It must have placeholder `context`. Default is `:CreateQAFromContext`.
  * `api_kwargs::NamedTuple`: Parameters that will be forwarded to the API endpoint.
  * `verbose::Bool`: If `true`, additional information like costs will be logged. Defaults to `true`.

# Returns

`Vector{QAEvalItem}`: A vector of `QAEvalItem` structs, each containing a source, context, question, and answer. Invalid or empty items are filtered out.

# Notes

  * The function internally uses `aiextract` to generate Q&A pairs based on the provided `qa_template`. So you can use any kwargs that you want.
  * Each `QAEvalItem` includes the context (document chunk), the generated question and answer, and the source.
  * The function tracks and reports the cost of AI calls if `verbose` is enabled.
  * Items where the question, answer, or context is empty are considered invalid and are filtered out.

# Examples

Creating Q&A evaluations from a set of document chunks:

```julia
doc_chunks = ["Text from document 1", "Text from document 2"]
sources = ["source1", "source2"]
qa_evals = build_qa_evals(doc_chunks, sources)
```
