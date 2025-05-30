```
write_embedding(
    emb::IndexedWordEmbedding,
    path::AbstractString;
    max_vocab_size::Union{Int,Nothing}=nothing,
    keep_words::Union{Vector{String},Nothing}=nothing
)::Nothing
```

The `write_embedding()` function saves an `IndexedWordEmbedding` object to a binary file specified by `path`. The vocabulary can be filtered with `keep_words` and limited to `max_vocab_size`.
