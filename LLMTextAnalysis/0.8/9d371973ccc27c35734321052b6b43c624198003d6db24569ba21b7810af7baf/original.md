```
TopicMetadata <: AbstractTopicMetadata
```

A struct representing the metadata of a specific topic extracted from a collection of documents.

# Fields

  * `index_id::Symbol`: Identifier for the topic.
  * `topic_level::Union{AbstractString, Int}`: The level of the topic in the hierarchy.
  * `topic_idx::Int`: Index of the topic.
  * `label::AbstractString`: Human-readable label of the topic. Defaults to `""`.
  * `summary::AbstractString`: Brief summary of the topic. Defaults to `""`.
  * `docs_idx::Vector{Int}`: Indices of documents belonging to this topic. Corresponds to positions in `index.docs`.
  * `center_doc_idx::Int`: Index of the central document in this topic. Corresponds to a position in `docs_idx` (not index!)
  * `samples_doc_idx::Vector{Int}`: Indices of representative documents. Corresponds to positions in `docs_idx` (not index!)
  * `keywords_idx::Vector{Int}`: Indices of specific keywords associated with this topic. Corresponds to positions in `index.keywords_vocab`.

# Example

```julia
topic = TopicMetadata(topic_level=1, topic_idx=5)
```
