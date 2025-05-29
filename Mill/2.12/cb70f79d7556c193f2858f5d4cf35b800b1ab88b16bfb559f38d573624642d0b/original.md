```
Mill.metadata(n::AbstractMillNode)
```

Return metadata stored in node `n`.

# Examples

```jldoctest
julia> Mill.metadata(ArrayNode([1 2; 3 4], ["foo", "bar"]))
2-element Vector{String}:
 "foo"
 "bar"

julia> Mill.metadata(BagNode(ArrayNode([1 2; 3 4]), [1, 2], ["metadata"]))
1-element Vector{String}:
 "metadata"
```

See also: [`Mill.data`](@ref), [`Mill.dropmeta`](@ref), [`Mill.metadata_getindex`](@ref).
