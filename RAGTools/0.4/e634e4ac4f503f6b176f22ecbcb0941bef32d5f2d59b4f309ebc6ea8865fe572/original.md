```
retrieve(
	retriever::AbstractRetriever,
	index::AbstractChunkIndex,
	question::AbstractString;
	verbose::Integer = 1,
	top_k::Integer = 100,
	top_n::Integer = 5,
	api_kwargs::NamedTuple = NamedTuple(),
	rephraser::AbstractRephraser = retriever.rephraser,
	rephraser_kwargs::NamedTuple = NamedTuple(),
	embedder::AbstractEmbedder = retriever.embedder,
	embedder_kwargs::NamedTuple = NamedTuple(),
	processor::AbstractProcessor = retriever.processor,
	processor_kwargs::NamedTuple = NamedTuple(),
	finder::AbstractSimilarityFinder = retriever.finder,
	finder_kwargs::NamedTuple = NamedTuple(),
	tagger::AbstractTagger = retriever.tagger,
	tagger_kwargs::NamedTuple = NamedTuple(),
	filter::AbstractTagFilter = retriever.filter,
	filter_kwargs::NamedTuple = NamedTuple(),
	reranker::AbstractReranker = retriever.reranker,
	reranker_kwargs::NamedTuple = NamedTuple(),
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...,
)
```

Retrieves the most relevant chunks from the index for the given question and returns them in the `RAGResult` object.

This is the main entry point for the retrieval stage of the RAG pipeline. It is often followed by `generate!` step.

Notes:

  * The default flow is `build_context!` -> `answer!` -> `refine!` -> `postprocess!`.

The arguments correspond to the steps of the retrieval process (rephrasing, embedding, finding similar docs, tagging, filtering by tags, reranking). You can customize each step by providing a new custom type that dispatches the corresponding function,  	eg, create your own type `struct MyReranker<:AbstractReranker end` and define the custom method for it `rerank(::MyReranker,...) = ...`.

Note: Discover available retrieval sub-types for each step with `subtypes(AbstractRephraser)` and similar for other abstract types.

If you're using locally-hosted models, you can pass the `api_kwargs` with the `url` field set to the model's URL and make sure to provide corresponding  	`model` kwargs to `rephraser`, `embedder`, and `tagger` to use the custom models (they make AI calls).

# Arguments

  * `retriever`: The retrieval method to use. Default is `SimpleRetriever` but could be `AdvancedRetriever` for more advanced retrieval.
  * `index`: The index that holds the chunks and sources to be retrieved from.
  * `question`: The question to be used for the retrieval.
  * `verbose`: If `>0`, it prints out verbose logging. Default is `1`. If you set it to `2`, it will print out logs for each sub-function.
  * `top_k`: The TOTAL number of closest chunks to return from `find_closest`. Default is `100`.  If there are multiple rephrased questions, the number of chunks per each item will be `top_k ÷ number_of_rephrased_questions`.
  * `top_n`: The TOTAL number of most relevant chunks to return for the context (from `rerank` step). Default is `5`.
  * `api_kwargs`: Additional keyword arguments to be passed to the API calls (shared by all `ai*` calls).
  * `rephraser`: Transform the question into one or more questions. Default is `retriever.rephraser`.
  * `rephraser_kwargs`: Additional keyword arguments to be passed to the rephraser.

```
- `model`: The model to use for rephrasing. Default is `PT.MODEL_CHAT`.
- `template`: The rephrasing template to use. Default is `:RAGQueryOptimizer` or `:RAGQueryHyDE` (depending on the `rephraser` selected).
```

  * `embedder`: The embedding method to use. Default is `retriever.embedder`.
  * `embedder_kwargs`: Additional keyword arguments to be passed to the embedder.
  * `processor`: The processor method to use when using Keyword-based index. Default is `retriever.processor`.
  * `processor_kwargs`: Additional keyword arguments to be passed to the processor.
  * `finder`: The similarity search method to use. Default is `retriever.finder`, often `CosineSimilarity`.
  * `finder_kwargs`: Additional keyword arguments to be passed to the similarity finder.
  * `tagger`: The tag generating method to use. Default is `retriever.tagger`.
  * `tagger_kwargs`: Additional keyword arguments to be passed to the tagger. Noteworthy arguments:

```
- `tags`: Directly provide the tags to use for filtering (can be String, Regex, or Vector{String}). Useful for `tagger = PassthroughTagger`.
```

  * `filter`: The tag matching method to use. Default is `retriever.filter`.
  * `filter_kwargs`: Additional keyword arguments to be passed to the tag filter.
  * `reranker`: The reranking method to use. Default is `retriever.reranker`.
  * `reranker_kwargs`: Additional keyword arguments to be passed to the reranker.

```
- `model`: The model to use for reranking. Default is `rerank-english-v2.0` if you use `reranker = CohereReranker()`.
```

  * `cost_tracker`: An atomic counter to track the cost of the retrieval. Default is `Threads.Atomic{Float64}(0.0)`.

See also: `SimpleRetriever`, `AdvancedRetriever`, `build_index`, `rephrase`, `get_embeddings`, `get_keywords`, `find_closest`, `get_tags`, `find_tags`, `rerank`, `RAGResult`.

# Examples

Find the 5 most relevant chunks from the index for the given question.

```julia
# assumes you have an existing index `index`
retriever = SimpleRetriever()

result = retrieve(retriever,
	index,
	"What is the capital of France?",
	top_n = 5)

# or use the default retriever (same as above)
result = retrieve(retriever,
	index,
	"What is the capital of France?",
	top_n = 5)
```

Apply more advanced retrieval with question rephrasing and reranking (requires `COHERE_API_KEY`). We will obtain top 100 chunks from embeddings (`top_k`) and top 5 chunks from reranking (`top_n`).

```julia
retriever = AdvancedRetriever()

result = retrieve(retriever, index, question; top_k=100, top_n=5)
```

You can use the `retriever` to customize your retrieval strategy or directly change the strategy types in the `retrieve` kwargs!

Example of using locally-hosted model hosted on `localhost:8080`:

```julia
retriever = SimpleRetriever()
result = retrieve(retriever, index, question;
	rephraser_kwargs = (; model = "custom"),
	embedder_kwargs = (; model = "custom"),
	tagger_kwargs = (; model = "custom"), api_kwargs = (;
		url = "http://localhost:8080"))
```
