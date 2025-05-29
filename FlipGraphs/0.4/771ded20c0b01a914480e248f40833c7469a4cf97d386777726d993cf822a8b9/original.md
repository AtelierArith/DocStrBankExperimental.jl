```
relative_degrees(g::TriangulatedPolygon, U::Vector{<:Integer}, V::Vector{<:Integer}) :: Vector{<:Integer}
```

Count, for each vertex in `U`, the number of incident edges, which are also incident to an edge in `V`.
