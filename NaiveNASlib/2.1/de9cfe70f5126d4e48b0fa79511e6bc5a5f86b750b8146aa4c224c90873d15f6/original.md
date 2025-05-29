```
inputs(v)
```

Return an Array of vertices which are input to the given vertex.

# Examples

```jldoctest
julia> using NaiveNASlib, NaiveNASlib.Extend

julia> inputs(CompVertex(identity, InputVertex(1)))
1-element Vector{AbstractVertex}:
 InputVertex(1)
```
