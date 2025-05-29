```
edges_inner(g::TriangulatedPolygon{T}) :: Vector{SimpleEdge{T}} where T<:Integer
```

Compute and return a list of all the edges in `g`. These are exactly the flippable edges in `g`.

Edges are not directed. It is, however, necessary for computations to define a source and a target.  For `TriangulatedPolygon`, the source will be the incident vertex with the smaller id.
