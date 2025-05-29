```
vertexsetsize(vertexset)
```

Return the dimension of the linearspace corresponding to given `vertexset`.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> vertexsetsize(VertexSet([[1, 2, 3], [4, 5]]))
5
```
