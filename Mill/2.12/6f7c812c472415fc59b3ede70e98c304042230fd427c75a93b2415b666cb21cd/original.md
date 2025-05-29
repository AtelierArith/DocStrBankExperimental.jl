```
ArrayNode(d::AbstractArray, m=nothing)
```

Construct a new [`ArrayNode`](@ref) with data `d` and metadata `m`.

# Examples

```jldoctest
julia> a = ArrayNode([1 2; 3 4; 5 6])
3×2 ArrayNode{Matrix{Int64}, Nothing}:
 1  2
 3  4
 5  6
```

See also: [`AbstractMillNode`](@ref), [`ArrayModel`](@ref).
