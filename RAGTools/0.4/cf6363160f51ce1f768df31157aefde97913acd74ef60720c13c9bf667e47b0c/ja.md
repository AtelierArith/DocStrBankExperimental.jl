```
build_index(
	indexer::KeywordsIndexer, files_or_docs::Vector{<:AbstractString};
	verbose::Integer = 1,
	extras::Union{Nothing, AbstractVector} = nothing,
	index_id = gensym("ChunkKeywordsIndex"),
	chunker::AbstractChunker = indexer.chunker,
	chunker_kwargs::NamedTuple = NamedTuple(),
	processor::AbstractProcessor = indexer.processor,
	processor_kwargs::NamedTuple = NamedTuple(),
	tagger::AbstractTagger = indexer.tagger,
	tagger_kwargs::NamedTuple = NamedTuple(),
	api_kwargs::NamedTuple = NamedTuple(),
	cost_tracker = Threads.Atomic{Float64}(0.0))
```

提供されたファイルまたは文書からキーワードベースの検索（BM25）をサポートする `ChunkKeywordsIndex` を構築します。
