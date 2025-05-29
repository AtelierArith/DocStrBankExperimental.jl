```
is_isomorphic(g1::TriangulatedPolygon, g2::TriangulatedPolygon, permutations::Vector{Vector{T}}) where T<:Integer
```

Check if `g2` is isomorphic to `g1` up to a relabeling of the vertices by one of the `permutations`.
