```
Mill.data(n::AbstractMillNode)
```

Return data stored in node `n`.

# Examples

```jldoctest
julia> Mill.data(ArrayNode([1 2; 3 4], "metadata"))
2×2 Matrix{Int64}:
 1  2
 3  4

julia> Mill.data(BagNode(ArrayNode([1 2; 3 4]), [1, 2], "metadata"))
2×2 ArrayNode{Matrix{Int64}, Nothing}:
 1  2
 3  4
```

See also: [`Mill.metadata`](@ref)
