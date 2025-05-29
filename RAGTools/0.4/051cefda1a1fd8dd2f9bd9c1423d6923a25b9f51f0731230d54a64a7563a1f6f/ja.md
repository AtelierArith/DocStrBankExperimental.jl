```
find_tags(method::AllTagFilter, index::AbstractChunkIndex,
	tag::Union{AbstractString, Regex}; kwargs...)

find_tags(method::AllTagFilter, index::AbstractChunkIndex,
	tags::Vector{T}; kwargs...) where {T <: Union{AbstractString, Regex}}
```

指定された `tag` または `tags` のすべてを持つチャンク（`index` 内のタグで表される）のインデックスを見つけます。
