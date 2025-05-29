```
airag(cfg::AbstractRAGConfig, index::AbstractDocumentIndex;
	question::AbstractString,
	verbose::Integer = 1, return_all::Bool = false,
	api_kwargs::NamedTuple = NamedTuple(),
	retriever::AbstractRetriever = cfg.retriever,
	retriever_kwargs::NamedTuple = NamedTuple(),
	generator::AbstractGenerator = cfg.generator,
	generator_kwargs::NamedTuple = NamedTuple(),
	cost_tracker = Threads.Atomic{Float64}(0.0))
```

High-level wrapper for Retrieval-Augmented Generation (RAG), it combines together the `retrieve` and `generate!` steps which you can customize if needed.

The simplest version first finds the relevant chunks in `index` for the `question` and then sends these chunks to the AI model to help with generating a response to the `question`.

To customize the components, replace the types (`retriever`, `generator`) of the corresponding step of the RAG pipeline - or go into sub-routines within the steps. Eg, use `subtypes(AbstractRetriever)` to find the available options.

# Arguments

  * `cfg::AbstractRAGConfig`: The configuration for the RAG pipeline. Defaults to `RAGConfig()`, where you can swap sub-types to customize the pipeline.
  * `index::AbstractDocumentIndex`: The chunk index to search for relevant text.
  * `question::AbstractString`: The question to be answered.
  * `return_all::Bool`: If `true`, returns the details used for RAG along with the response.
  * `verbose::Integer`: If `>0`, enables verbose logging. The higher the number, the more nested functions will log.
  * `api_kwargs`: API parameters that will be forwarded to ALL of the API calls (`aiembed`, `aigenerate`, and `aiextract`).
  * `retriever::AbstractRetriever`: The retriever to use for finding relevant chunks. Defaults to `cfg.retriever`, eg, `SimpleRetriever` (with no question rephrasing).
  * `retriever_kwargs::NamedTuple`: API parameters that will be forwarded to the `retriever` call. Examples of important ones:

```
- `top_k::Int`: Number of top candidates to retrieve based on embedding similarity.
- `top_n::Int`: Number of candidates to return after reranking.
- `tagger::AbstractTagger`: Tagger to use for tagging the chunks. Defaults to `NoTagger()`.
- `tagger_kwargs::NamedTuple`: API parameters that will be forwarded to the `tagger` call. You could provide the explicit tags directly with `PassthroughTagger` and `tagger_kwargs = (; tags = ["tag1", "tag2"])`.
```

  * `generator::AbstractGenerator`: The generator to use for generating the answer. Defaults to `cfg.generator`, eg, `SimpleGenerator`.
  * `generator_kwargs::NamedTuple`: API parameters that will be forwarded to the `generator` call. Examples of important ones:

```
- `answerer_kwargs::NamedTuple`: API parameters that will be forwarded to the `answerer` call. Examples:
	- `model`: The model to use for generating the answer. Defaults to `PT.MODEL_CHAT`.
	- `template`: The template to use for the `aigenerate` function. Defaults to `:RAGAnswerFromContext`.
- `refiner::AbstractRefiner`: The method to use for refining the answer. Defaults to `generator.refiner`, eg, `NoRefiner`.
- `refiner_kwargs::NamedTuple`: API parameters that will be forwarded to the `refiner` call.
	- `model`: The model to use for generating the answer. Defaults to `PT.MODEL_CHAT`.
	- `template`: The template to use for the `aigenerate` function. Defaults to `:RAGAnswerRefiner`.
```

  * `cost_tracker`: An atomic counter to track the total cost of the operations (if you want to track the cost of multiple pipeline runs - it passed around in the pipeline).

# Returns

  * If `return_all` is `false`, returns the generated message (`msg`).
  * If `return_all` is `true`, returns the detail of the full pipeline in `RAGResult` (see the docs).

See also `build_index`, `retrieve`, `generate!`, `RAGResult`, `getpropertynested`, `setpropertynested`, `merge_kwargs_nested`, `ChunkKeywordsIndex`.

# Examples

Using `airag` to get a response for a question:

```julia
index = build_index(...)  # create an index
question = "How to make a barplot in Makie.jl?"
msg = airag(index; question)
```

To understand the details of the RAG process, use `return_all=true`

```julia
msg, details = airag(index; question, return_all = true)
# details is a RAGDetails object with all the internal steps of the `airag` function
```

You can also pretty-print `details` to highlight generated text vs text that is supported by context. It also includes annotations of which context was used for each part of the response (where available).

```julia
PT.pprint(details)
```

Example with advanced retrieval (with question rephrasing and reranking (requires `COHERE_API_KEY`). We will obtain top 100 chunks from embeddings (`top_k`) and top 5 chunks from reranking (`top_n`). In addition, it will be done with a "custom" locally-hosted model.

```julia
cfg = RAGConfig(; retriever = AdvancedRetriever())

# kwargs will be big and nested, let's prepare them upfront
# we specify "custom" model for each component that calls LLM
kwargs = (
	retriever_kwargs = (;
		top_k = 100,
		top_n = 5,
		rephraser_kwargs = (;
			model = "custom"),
		embedder_kwargs = (;
			model = "custom"),
		tagger_kwargs = (;
			model = "custom")),
	generator_kwargs = (;
		answerer_kwargs = (;
			model = "custom"),
		refiner_kwargs = (;
			model = "custom")),
	api_kwargs = (;
		url = "http://localhost:8080"))

result = airag(cfg, index, question; kwargs...)
```

If you want to use hybrid retrieval (embeddings + BM25), you can easily create an additional index based on keywords  and pass them both into a `MultiIndex`. 

You need to provide an explicit config, so the pipeline knows how to handle each index in the search similarity phase (`finder`).

```julia
index = # your existing index

# create the multi-index with the keywords index
index_keywords = ChunkKeywordsIndex(index)
multi_index = MultiIndex([index, index_keywords])

# define the similarity measures for the indices that you have (same order)
finder = RT.MultiFinder([RT.CosineSimilarity(), RT.BM25Similarity()])
cfg = RAGConfig(; retriever=AdvancedRetriever(; processor=RT.KeywordsProcessor(), finder))

# Run the pipeline with the new hybrid retrieval (return the `RAGResult` to see the details)
result = airag(cfg, multi_index; question, return_all=true)

# Pretty-print the result
PT.pprint(result)
```

For easier manipulation of nested kwargs, see utilities `getpropertynested`, `setpropertynested`, `merge_kwargs_nested`.
