```
Mill.metadata(n::AbstractMillNode)
```

ノード `n` に格納されているメタデータを返します。

# 例

```jldoctest
julia> Mill.metadata(ArrayNode([1 2; 3 4], ["foo", "bar"]))
2-element Vector{String}:
 "foo"
 "bar"

julia> Mill.metadata(BagNode(ArrayNode([1 2; 3 4]), [1, 2], ["metadata"]))
1-element Vector{String}:
 "metadata"
```

関連情報: [`Mill.data`](@ref), [`Mill.dropmeta`](@ref), [`Mill.metadata_getindex`](@ref).
