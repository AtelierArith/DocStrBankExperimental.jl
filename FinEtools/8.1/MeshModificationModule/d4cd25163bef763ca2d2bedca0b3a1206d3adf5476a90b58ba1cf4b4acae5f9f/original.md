```
mergenmeshes(meshes::Array{Tuple{FENodeSet{T},AbstractFESet}}, tolerance::T) where {T<:Number}
```

Merge several meshes together.

The meshes are glued together by merging the nodes that fall within a box of size `tolerance`. If `tolerance` is set to zero, no merging of nodes is performed; the nodes from the meshes are simply concatenated together.

# Output

The merged node set, `fens`, and an array of finite element sets with renumbered  connectivities are returned.
