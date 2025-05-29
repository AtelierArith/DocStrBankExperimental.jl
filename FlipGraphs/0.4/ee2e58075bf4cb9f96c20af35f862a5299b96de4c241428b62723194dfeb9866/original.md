```
vertices(D::DeltaComplex, d::DualEdge) :: Tuple{TriFace, TriFace}
```

Return both vertices(`TriFace`s) adjacent to the dual edge `d`.

The first `TriFace` is on the left of the edge, and the second one on the right of the edge.
