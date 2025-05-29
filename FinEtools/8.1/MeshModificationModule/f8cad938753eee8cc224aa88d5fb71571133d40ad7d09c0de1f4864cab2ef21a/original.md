```
mergenodes(fens::FENodeSet{T}, fes::AbstractFESet, tolerance::T) where {T<:Number}
```

Merge together nodes of a single node set.

Merge by gluing together nodes from a single node set located within tolerance of each other. The nodes are glued together by merging the nodes that fall within a box of size `tolerance`. The merged node set, `fens`, and the finite element set, `fes`, with renumbered  connectivities are returned.

Warning: This tends to be an expensive operation!
