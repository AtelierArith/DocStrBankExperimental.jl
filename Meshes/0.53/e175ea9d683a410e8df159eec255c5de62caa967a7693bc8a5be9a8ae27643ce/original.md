```
HalfEdge(head, elem, prev, next, half)
```

Stores the indices of the `head` vertex, the `prev` and `next` edges in the left `elem`, and the opposite `half`-edge. For some half-edges the `elem` may be `nothing`, e.g. border edges of the mesh.

See [`HalfEdgeTopology`](@ref) for more details.
