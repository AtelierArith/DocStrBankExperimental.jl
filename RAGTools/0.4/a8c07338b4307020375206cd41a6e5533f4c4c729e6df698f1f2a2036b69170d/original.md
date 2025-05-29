```
get_tags(tagger::OpenTagger, docs::AbstractVector{<:AbstractString};
	verbose::Bool = true,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...)
```

Extracts "tags" (metadata/keywords) from a vector of `docs` using the provided model (kwarg `model`).

# Arguments

  * `docs`: A vector of strings to be embedded.
  * `verbose`: A boolean flag for verbose output. Default is `true`.
  * `model`: The model to use for tags extraction. Default is `PT.MODEL_CHAT`.
  * `template`: A template to be used for tags extraction. Default is `:RAGExtractMetadataShort`.
  * `cost_tracker`: A `Threads.Atomic{Float64}` object to track the total cost of the API calls. Useful to pass the total cost to the parent call.
