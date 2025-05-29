```
metadata_getindex(x, i::Integer)
metadata_getindex(x, i::VecOrRange{<:Integer})
```

Index into metadata `x`. In [`Mill.jl`](@ref), it is assumed that the second or last dimension indexes into observations, whichever is smaller. This function can be used when implementing custom subtypes of [`AbstractMillNode`](@ref).

# Examples

```jldoctest
julia> Mill.metadata_getindex(["foo", "bar", "baz"], 2)
"bar"

julia> Mill.metadata_getindex(["foo", "bar", "baz"], 2:3)
2-element Vector{String}:
 "bar"
 "baz"

julia> Mill.metadata_getindex([1 2 3; 4 5 6], 2)
2-element Vector{Int64}:
 2
 5

julia> Mill.metadata_getindex([1 2 3; 4 5 6], [1, 3])
2×2 Matrix{Int64}:
 1  3
 4  6
```

See also: [`Mill.metadata`](@ref), [`Mill.dropmeta`](@ref).
