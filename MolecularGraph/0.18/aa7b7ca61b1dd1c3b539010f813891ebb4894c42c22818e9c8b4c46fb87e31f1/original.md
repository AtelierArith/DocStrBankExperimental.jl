```
fused_rings(mol::SimpleMolGraph{T}) -> Vector{Vector{T}}
```

Return vectors of fused ring node sets.

A fused ring is defined as a 2-edge connected components in terms of graph theory. Spirocyclic structures are considered to be part of a fused ring.
