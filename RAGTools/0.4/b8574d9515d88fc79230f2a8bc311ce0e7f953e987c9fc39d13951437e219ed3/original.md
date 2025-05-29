```
get_embeddings(embedder::BinaryBatchEmbedder, docs::AbstractVector{<:AbstractString};
	verbose::Bool = true,
	model::AbstractString = PT.MODEL_EMBEDDING,
	truncate_dimension::Union{Int, Nothing} = nothing,
	return_type::Type = Matrix{Bool},
	cost_tracker = Threads.Atomic{Float64}(0.0),
	target_batch_size_length::Int = 80_000,
	ntasks::Int = 4 * Threads.nthreads(),
	kwargs...)
```

Embeds a vector of `docs` using the provided model (kwarg `model`) in a batched manner and then returns the binary embeddings matrix - `BinaryBatchEmbedder`.

`BinaryBatchEmbedder` tries to batch embedding calls for roughly 80K characters per call (to avoid exceeding the API rate limit) to reduce network latency.

# Notes

  * `docs` are assumed to be already chunked to the reasonable sizes that fit within the embedding context limit.
  * If you get errors about exceeding input sizes, first check the `max_length` in your chunks.  If that does NOT resolve the issue, try reducing the `target_batch_size_length` parameter (eg, 10_000) and number of tasks `ntasks=1`.  Some providers cannot handle large batch sizes.

# Arguments

  * `docs`: A vector of strings to be embedded.
  * `verbose`: A boolean flag for verbose output. Default is `true`.
  * `model`: The model to use for embedding. Default is `PT.MODEL_EMBEDDING`.
  * `truncate_dimension`: The dimensionality of the embeddings to truncate to. Default is `nothing`.
  * `return_type`: The type of the returned embeddings matrix. Default is `Matrix{Bool}`. Choose `BitMatrix` to minimize storage requirements, `Matrix{Bool}` to maximize performance in elementwise-ops.
  * `cost_tracker`: A `Threads.Atomic{Float64}` object to track the total cost of the API calls. Useful to pass the total cost to the parent call.
  * `target_batch_size_length`: The target length (in characters) of each batch of document chunks sent for embedding. Default is 80_000 characters. Speeds up embedding process.
  * `ntasks`: The number of tasks to use for asyncmap. Default is 4 * Threads.nthreads().
