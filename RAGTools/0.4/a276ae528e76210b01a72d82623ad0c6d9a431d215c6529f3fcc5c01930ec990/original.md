```
ChunkEmbeddingsIndex
```

Main struct for storing document chunks and their embeddings. It also stores tags  and sources for each chunk.

Previously, this struct was called `ChunkIndex`.

# Fields

  * `id::Symbol`: unique identifier of each index (to ensure we're using the right index with `CandidateChunks`)
  * `chunks::Vector{<:AbstractString}`: underlying document chunks / snippets
  * `embeddings::Union{Nothing, Matrix{<:Real}}`: for semantic search
  * `tags::Union{Nothing, AbstractMatrix{<:Bool}}`: for exact search, filtering, etc.    This is often a sparse matrix indicating which chunks have the given `tag`    (see `tag_vocab` for the position lookup)
  * `tags_vocab::Union{Nothing, Vector{<:AbstractString}}`: vocabulary for the `tags`    matrix (each column in `tags` is one item in `tags_vocab` and rows are the chunks)
  * `sources::Vector{<:AbstractString}`: sources of the chunks
  * `extras::Union{Nothing, AbstractVector}`: additional data, eg, metadata, source code, etc.
