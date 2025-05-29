```
SnowRAG
```

Type designed for displaying the RAG conversation in Spehulak.

# Fields

  * `conv_main`: The main conversation (what user sees)
  * `conv_answer`: The answer conversation (default LLM chain)
  * `conv_final_answer`: The final answer conversation (if we used `refine!` functionality)
  * `has_refined_answer`: Whether the answer has been refined (`refine!` functionality)
  * `context`: The context used to answer the question
  * `sources`: The sources used to answer the question
  * `emb_stats`: The embedding candidates statistics (to understand retrieval performance)
  * `rerank_stats`: The reranking candidates statistics (to understand reranking performance)
  * `meta`: The metadata from the first message (if it's a tracer message)
