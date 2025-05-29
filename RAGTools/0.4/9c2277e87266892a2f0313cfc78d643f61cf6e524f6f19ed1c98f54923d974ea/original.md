```
SimpleBM25Retriever <: AbstractRetriever
```

Keyword-based implementation for `retrieve`. It does a simple similarity search via `BM25Similarity` and returns the results.

Make sure to use consistent `processor` and `tagger` with the Preparation Stage (`build_index`)!

# Fields

  * `rephraser::AbstractRephraser`: the rephrasing method, dispatching `rephrase` - uses `NoRephraser`
  * `embedder::AbstractEmbedder`: the embedding method, dispatching `get_embeddings` (see Preparation Stage for more details) - uses `NoEmbedder`
  * `processor::AbstractProcessor`: the processor method, dispatching `get_keywords` (see Preparation Stage for more details) - uses `KeywordsProcessor`
  * `finder::AbstractSimilarityFinder`: the similarity search method, dispatching `find_closest` - uses `CosineSimilarity`
  * `tagger::AbstractTagger`: the tag generating method, dispatching `get_tags` (see Preparation Stage for more details) - uses `NoTagger`
  * `filter::AbstractTagFilter`: the tag matching method, dispatching `find_tags` - uses `NoTagFilter`
  * `reranker::AbstractReranker`: the reranking method, dispatching `rerank` - uses `NoReranker`
