```
ChunkKeywordsIndex
```

Struct for storing chunks of text and associated keywords for BM25 similarity search.

# Fields

  * `id::Symbol`: unique identifier of each index (to ensure we're using the right    index with `CandidateChunks`)
  * `chunks::Vector{<:AbstractString}`: underlying document chunks / snippets
  * `chunkdata::Union{Nothing, AbstractMatrix{<:Real}}`: for similarity search,    assumed to be `DocumentTermMatrix`
  * `tags::Union{Nothing, AbstractMatrix{<:Bool}}`: for exact search, filtering, etc.    This is often a sparse matrix indicating which chunks have the given `tag`    (see `tag_vocab` for the position lookup)
  * `tags_vocab::Union{Nothing, Vector{<:AbstractString}}`: vocabulary for the `tags`    matrix (each column in `tags` is one item in `tags_vocab` and rows are the chunks)
  * `sources::Vector{<:AbstractString}`: sources of the chunks
  * `extras::Union{Nothing, AbstractVector}`: additional data, eg, metadata, source code, etc.

# Example

We can easily create a keywords-based index from a standard embeddings-based index.

```julia

# Let's assume we have a standard embeddings-based index
index = build_index(SimpleIndexer(), texts; chunker_kwargs = (; max_length=10))

# Creating an additional index for keyword-based search (BM25), is as simple as
index_keywords = ChunkKeywordsIndex(index)

# We can immediately create a MultiIndex (a hybrid index holding both indices)
multi_index = MultiIndex([index, index_keywords])

```

You can also build the index via build_index

```julia
# given some sentences and sources
index_keywords = build_index(KeywordsIndexer(), sentences; chunker_kwargs=(; sources))

# Retrive closest chunks with
retriever = SimpleBM25Retriever()
result = retrieve(retriever, index_keywords, "What are the best practices for parallel computing in Julia?")
result.context
```

If you want to use airag, don't forget to specify the config to make sure keywords  are processed (ie, tokenized) and that BM25 is used for searching candidates

```julia
cfg = RAGConfig(; retriever = SimpleBM25Retriever());
airag(cfg, index_keywords;
	question = "What are the best practices for parallel computing in Julia?")
```
