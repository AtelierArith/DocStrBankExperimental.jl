```
find_tags(method::AllTagFilter, index::AbstractChunkIndex,
	tag::Union{AbstractString, Regex}; kwargs...)

find_tags(method::AllTagFilter, index::AbstractChunkIndex,
	tags::Vector{T}; kwargs...) where {T <: Union{AbstractString, Regex}}
```

Finds the indices of chunks (represented by tags in `index`) that have ALL OF the specified `tag` or `tags`.
