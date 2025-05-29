```
find_tags(method::NoTagFilter, index::AbstractChunkIndex,
	tags::Union{T, AbstractVector{<:T}}; kwargs...) where {T <:
														   Union{
	AbstractString, Regex, Nothing}}
	tags; kwargs...)
```

Returns all chunks in the index, ie, no filtering, so we simply return `nothing` (easier for dispatch).
