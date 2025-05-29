```
build_clusters!(index::AbstractDocumentIndex; k::Union{Int, Nothing} = nothing,
    h::Union{Float64, Nothing} = nothing,
    verbose::Bool = true, add_label::Bool = true, add_summary::Bool = false,
    labeler_kwargs::NamedTuple = NamedTuple(),
    cluster_kwargs...)
```

Performs automatic clustering on the document index and builds topics at different levels.

# Arguments

  * `index`: The document index.
  * `k`: Number of clusters to cut at.
  * `h`: Height to cut the dendrogram at. See `?Clustering.hclust` for more details.
  * `verbose`: Flag to enable INFO logging.
  * `add_label`: Flag to enable topic labeling, ie, call LLM to generate topic label.
  * `add_summary`: Flag to enable topic summarization, ie, call LLM to generate topic summary.
  * `labeler_kwargs`: Keyword arguments to pass to the LLM labeler. See `?build_topic` for more details on available arguments.
  * `cluster_kwargs`: All remaining arguments will be passed to `Clustering.hclust`. See `?Clustering.hclust` for more details on available arguments.

# Returns

  * The updated index with clustering information and topic metadata.

# Example

```julia
index = build_index(["Doc 1", "Doc 2"])
clustered_index = build_clusters!(index, k=2)
```
