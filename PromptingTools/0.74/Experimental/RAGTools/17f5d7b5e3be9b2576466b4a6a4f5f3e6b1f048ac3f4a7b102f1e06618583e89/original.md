```
PT.pprint(
    io::IO, r::AbstractRAGResult; add_context::Bool = false,
    text_width::Int = displaysize(io)[2], annotater_kwargs...)
```

Pretty print the RAG result `r` to the given `io` stream. 

If `add_context` is `true`, the context will be printed as well. The `text_width` parameter can be used to control the width of the output.

You can provide additional keyword arguments to the annotater, eg, `add_sources`, `add_scores`, `min_score`, etc. See `annotate_support` for more details.
