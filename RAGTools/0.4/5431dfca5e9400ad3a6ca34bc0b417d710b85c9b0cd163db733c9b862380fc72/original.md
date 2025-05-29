```
build_index(
	indexer::AbstractIndexBuilder, files_or_docs::Vector{<:AbstractString};
	verbose::Integer = 1,
	extras::Union{Nothing, AbstractVector} = nothing,
	index_id = gensym("ChunkEmbeddingsIndex"),
	chunker::AbstractChunker = indexer.chunker,
	chunker_kwargs::NamedTuple = NamedTuple(),
	embedder::AbstractEmbedder = indexer.embedder,
	embedder_kwargs::NamedTuple = NamedTuple(),
	tagger::AbstractTagger = indexer.tagger,
	tagger_kwargs::NamedTuple = NamedTuple(),
	api_kwargs::NamedTuple = NamedTuple(),
	cost_tracker = Threads.Atomic{Float64}(0.0))
```

Build an INDEX for RAG (Retriever-Augmented Generation) applications from the provided file paths.  INDEX is a object storing the document chunks and their embeddings (and potentially other information).

The function processes each file or document (depending on `chunker`), splits its content into chunks, embeds these chunks,  optionally extracts metadata, and then combines this information into a retrievable index.

Define your own methods via `indexer` and its subcomponents (`chunker`, `embedder`, `tagger`).

# Arguments

  * `indexer::AbstractIndexBuilder`: The indexing logic to use. Default is `SimpleIndexer()`.
  * `files_or_docs`: A vector of valid file paths OR string documents to be indexed (chunked and embedded). Specify which mode to use via `chunker`.
  * `verbose`: An Integer specifying the verbosity of the logs. Default is `1` (high-level logging). `0` is disabled.
  * `extras`: An optional vector of extra information to be stored with each chunk. Default is `nothing`.
  * `index_id`: A unique identifier for the index. Default is a generated symbol.
  * `chunker`: The chunker logic to use for splitting the documents. Default is `TextChunker()`.
  * `chunker_kwargs`: Parameters to be provided to the `get_chunks` function. Useful to change the `separators` or `max_length`.

      * `sources`: A vector of strings indicating the source of each chunk. Default is equal to `files_or_docs`.
  * `embedder`: The embedder logic to use for embedding the chunks. Default is `BatchEmbedder()`.
  * `embedder_kwargs`: Parameters to be provided to the `get_embeddings` function. Useful to change the `target_batch_size_length` or reduce asyncmap tasks `ntasks`.

      * `model`: The model to use for embedding. Default is `PT.MODEL_EMBEDDING`.
  * `tagger`: The tagger logic to use for extracting tags from the chunks. Default is `NoTagger()`, ie, skip tag extraction. There are also `PassthroughTagger` and `OpenTagger`.
  * `tagger_kwargs`: Parameters to be provided to the `get_tags` function.

      * `model`: The model to use for tags extraction. Default is `PT.MODEL_CHAT`.
      * `template`: A template to be used for tags extraction. Default is `:RAGExtractMetadataShort`.
      * `tags`: A vector of vectors of strings directly providing the tags for each chunk. Applicable for `tagger::PasstroughTagger`.
  * `api_kwargs`: Parameters to be provided to the API endpoint. Shared across all API calls if provided.
  * `cost_tracker`: A `Threads.Atomic{Float64}` object to track the total cost of the API calls. Useful to pass the total cost to the parent call.

# Returns

  * `ChunkEmbeddingsIndex`: An object containing the compiled index of chunks, embeddings, tags, vocabulary, and sources.

See also: `ChunkEmbeddingsIndex`, `get_chunks`, `get_embeddings`, `get_tags`, `CandidateChunks`, `find_closest`, `find_tags`, `rerank`, `retrieve`, `generate!`, `airag`

# Examples

```julia
# Default is loading a vector of strings and chunking them (`TextChunker()`)
index = build_index(SimpleIndexer(), texts; chunker_kwargs = (; max_length=10))

# Another example with tags extraction, splitting only sentences and verbose output
# Assuming `test_files` is a vector of file paths
indexer = SimpleIndexer(chunker=FileChunker(), tagger=OpenTagger())
index = build_index(indexer, test_files; 
		chunker_kwargs(; separators=[". "]), verbose=true)
```

# Notes

  * If you get errors about exceeding embedding input sizes, first check the `max_length` in your chunks.  If that does NOT resolve the issue, try changing the `embedding_kwargs`.  In particular, reducing the `target_batch_size_length` parameter (eg, 10_000) and number of tasks `ntasks=1`.  Some providers cannot handle large batch sizes (eg, Databricks).
