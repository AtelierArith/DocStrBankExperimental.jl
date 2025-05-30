```
read_embedding(
    path::AbstractString;
    delim::AbstractChar=' ',
    max_vocab_size::Union{Int,Nothing}=nothing,
    keep_words::Union{Vector{String},Nothing}=nothing
)::WordEmbedding
```

The function `read_embedding()` is used to read embedding files in a conventional way. It creates a `WordEmbedding` object using CSV.jl. The function takes a path to the local embedding vector as an argument and has two optional keyword arguments: `max_vocab_size` and `keep_words`.

If `max_vocab_size` is specified, the function limits the size of the vector to that number. If a vector `keep_words` is provided, it only keeps those words. If a word in `keep_words` is not found, the function returns a zero vector for that word.

If the file is a `WordEmbedding` object within a Julia binary file (with extension `.jld` or in specific formats `.emb` or `.wem`), the entire embedding is loaded, and keyword arguments are not applicable. You can also use the `read_emb()` function directly on binary files. For pre-saved indexed embeddings, `read_indexed_emb()` currently is the only option.

# Notes

Note that if you set `max_vocab_size` ≥ 45k, the function's performance may suffer compared to `limit(read_embedding(path), max_vocab_size)`. This is because using this parameter restricts CSV.jl jobs to a single thread. However, using `max_vocab_size` results in less memory allocation than reading the entire file.

In addition, using `keep_words` with as many as 1k selected words is significantly slower yet more memory-efficient compared to `subspace(index(read_embedding(path)), keep_words)`. For 10k selected words reading may take more than 5 seconds.
