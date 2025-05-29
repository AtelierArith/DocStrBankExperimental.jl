```
prepare_plot!(index::AbstractDocumentIndex; verbose::Bool=true, kwargs...) -> AbstractDocumentIndex
```

Prepares the 2D UMAP plot data for a given document index.

# Arguments

  * `index`: The document index to prepare plot data for.
  * `verbose`: Flag to enable INFO logging.

# Returns

  * The updated index with `plot_data` field populated.

# Example

```julia
index = build_index(["Some text", "More text"])
prepared_index = prepare_plot!(index)
```
