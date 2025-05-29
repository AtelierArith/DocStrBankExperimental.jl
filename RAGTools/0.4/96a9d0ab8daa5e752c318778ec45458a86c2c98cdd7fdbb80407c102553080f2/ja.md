```
find_tags(method::NoTagFilter, index::AbstractChunkIndex,
	tags::Union{T, AbstractVector{<:T}}; kwargs...) where {T <:
														   Union{
	AbstractString, Regex, Nothing}}
	tags; kwargs...)
```

インデックス内のすべてのチャンクを返します。つまり、フィルタリングは行わず、単に `nothing` を返します（ディスパッチが簡単になります）。
