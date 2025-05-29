```
has_vertex(G::FlipGraphPlanar, g::TriangulatedPolygon) :: Bool
```

Return `true` if `g` is a vertex in `G`. 

If `G` is a modular flip graph, this will only return `true` if `g` is the proper representant of the vertex.
