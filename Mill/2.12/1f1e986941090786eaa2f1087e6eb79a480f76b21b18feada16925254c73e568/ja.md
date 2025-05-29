```
dropmeta(n:AbstractMillNode)
```

データノード `n` に保存されているメタデータを削除します（再帰的に）。

# 例

```jldoctest
julia> n1 = ArrayNode(NGramMatrix(["foo", "bar"]), ["metafoo", "metabar"])
2053×2 ArrayNode{NGramMatrix{String, Vector{String}, Int64}, Vector{String}}:
 "foo"
 "bar"

julia> n2 = dropmeta(n1)
2053×2 ArrayNode{NGramMatrix{String, Vector{String}, Int64}, Nothing}:
 "foo"
 "bar"

julia> isnothing(Mill.metadata(n2))
true
```

参照: [`Mill.metadata`](@ref), [`Mill.metadata_getindex`](@ref).
