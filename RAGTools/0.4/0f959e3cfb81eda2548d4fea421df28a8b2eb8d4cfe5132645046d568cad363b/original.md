```
RAGResult
```

A struct for debugging RAG answers. It contains the question, answer, context,  and the candidate chunks at each step of the RAG pipeline.

Think of the flow as `question` -> `rephrased_questions` -> `answer` -> `final_answer`  with the context and candidate chunks helping along the way.

# Fields

  * `question::AbstractString`: the original question
  * `rephrased_questions::Vector{<:AbstractString}`: a vector of rephrased questions (eg, HyDe, Multihop, etc.)
  * `answer::AbstractString`: the generated answer
  * `final_answer::AbstractString`: the refined final answer (eg, after CorrectiveRAG),

```
also considered the FINAL answer (it must be always available)
```

  * `context::Vector{<:AbstractString}`: the context used for retrieval (ie, the vector

```
of chunks and their surrounding window if applicable)
```

  * `sources::Vector{<:AbstractString}`: the sources of the context (for the original matched chunks)
  * `emb_candidates::CandidateChunks`: the candidate chunks from the embedding index (from `find_closest`)
  * `tag_candidates::Union{Nothing, CandidateChunks}`: the candidate chunks from the tag index (from `find_tags`)
  * `filtered_candidates::CandidateChunks`: the filtered candidate chunks (intersection

```
of `emb_candidates` and `tag_candidates`)
```

  * `reranked_candidates::CandidateChunks`: the reranked candidate chunks (from `rerank`)
  * `conversations::Dict{Symbol,Vector{<:AbstractMessage}}`: the conversation history for

```
AI steps of the RAG pipeline, use keys that correspond to the function names, eg, `:answer` or `:refine`
```

See also: `pprint` (pretty printing), `annotate_support` (for annotating the answer)
