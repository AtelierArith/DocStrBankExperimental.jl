```
MultiIndex
```

Composite index that stores multiple ChunkIndex objects and their embeddings.

# Fields

  * `id::Symbol`: unique identifier of each index (to ensure we're using the right index with `CandidateChunks`)
  * `indexes::Vector{<:AbstractChunkIndex}`: the indexes to be combined

Use accesor `indexes` to access the individual indexes.

# Examples

We can create a `MultiIndex` from a vector of `AbstractChunkIndex` objects.

```julia
index = build_index(SimpleIndexer(), texts; chunker_kwargs = (; sources))
index_keywords = ChunkKeywordsIndex(index) # same chunks as above but adds BM25 instead of embeddings

multi_index = MultiIndex([index, index_keywords])
```

To use `airag` with different types of indices, we need to specify how to find the closest items for each index

```julia
# Cosine similarity for embeddings and BM25 for keywords, same order as indexes in MultiIndex
finder = RT.MultiFinder([RT.CosineSimilarity(), RT.BM25Similarity()])

# Notice that we add `processor` to make sure keywords are processed (ie, tokenized) as well
cfg = RAGConfig(; retriever = SimpleRetriever(; processor = RT.KeywordsProcessor(), finder))

# Ask questions
msg = airag(cfg, multi_index; question = "What are the best practices for parallel computing in Julia?")
pprint(msg) # prettify the answer
```
