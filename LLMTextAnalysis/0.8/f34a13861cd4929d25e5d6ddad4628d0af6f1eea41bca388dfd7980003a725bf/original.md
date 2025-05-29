```
build_index(docs::Vector{<:AbstractString}; verbose::Bool = true,
index_id::Symbol = gensym("DocIndex"), aiembed_kwargs::NamedTuple = NamedTuple(),
keyword_kwargs::NamedTuple = NamedTuple(), kwargs...)
```

Builds an index of the given documents, including their embeddings and extracted keywords.

# Arguments

  * `docs`: Collection of documents to index. If you have only one large document, consider splitting it into smaller chunks with `PromptingTools.split_by_length`.
  * `verbose`: Flag to enable INFO logging.
  * `index_id`: Identifier for the document index. Useful if there will be multiple indices.
  * `aiembed_kwargs`: Additional arguments for `PromptingTools.aiembed`. See `?aiembed` for more details.
  * `keyword_kwargs`: Additional arguments for keyword extraction. See `?build_keywords` for more details.

# Returns

  * An instance of `DocIndex` containing information about the documents, embeddings, keywords, etc.

# Example

```julia
docs = ["First document text", "Second document text"]
index = build_index(docs)
```
