```
vlist(vset)
```

Returns the list of vertices for given `vset` of type `VertexSet`.

```jldoctest; setup = :(using QSWalk)
julia> vset = VertexSet([[1], [2, 3, 4], [5, 6, 7], [8, 9]])
VertexSet(Vertex[Vertex([1]), Vertex([2, 3, 4]), Vertex([5, 6, 7]), Vertex([8, 9])])

julia> vlist(vset)
4-element Array{Vertex,1}:
 Vertex([1])
 Vertex([2, 3, 4])
 Vertex([5, 6, 7])
 Vertex([8, 9])
```
