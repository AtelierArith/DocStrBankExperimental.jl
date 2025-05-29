```
AdvancedRetriever <: AbstractRetriever
```

Dispatch for `retrieve` with advanced retrieval methods to improve result quality. Compared to SimpleRetriever, it adds rephrasing the query and reranking the results.

# Fields

  * `rephraser::AbstractRephraser`: the rephrasing method, dispatching `rephrase` - uses `HyDERephraser`
  * `embedder::AbstractEmbedder`: the embedding method, dispatching `get_embeddings` (see Preparation Stage for more details) - uses `BatchEmbedder`
  * `processor::AbstractProcessor`: the processor method, dispatching `get_keywords` (see Preparation Stage for more details) - uses `NoProcessor`
  * `finder::AbstractSimilarityFinder`: the similarity search method, dispatching `find_closest` - uses `CosineSimilarity`
  * `tagger::AbstractTagger`: the tag generating method, dispatching `get_tags` (see Preparation Stage for more details) - uses `NoTagger`
  * `filter::AbstractTagFilter`: the tag matching method, dispatching `find_tags` - uses `NoTagFilter`
  * `reranker::AbstractReranker`: the reranking method, dispatching `rerank` - uses `CohereReranker`
