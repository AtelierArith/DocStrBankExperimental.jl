```
mergemeshes(
    fens1::FENodeSet{T},
    fes1::T1,
    fens2::FENodeSet{T},
    fes2::T2,
    tolerance::T,
) where {T, T1<:AbstractFESet, T2<:AbstractFESet}
```

Merge together two meshes.

Merge two meshes together by gluing together nodes within tolerance. The two meshes, `fens1`, `fes1`, and `fens2`, `fes2`, are glued together by merging the nodes that fall within a box of size `tolerance`. If `tolerance` is set to zero, no merging of nodes is performed; the two meshes are simply concatenated together.

The merged node set, `fens`, and the two finite element sets with renumbered  connectivities are returned.

Important notes: On entry into this function the connectivity of `fes1` point into `fens1` and the connectivity of `fes2` point into `fens2`. After this function returns the connectivity of both `fes1` and `fes2` point into `fens`. The order of the nodes of the node set `fens1` in the resulting set `fens` will have changed, whereas the order of the nodes of the node set `fens2` is are guaranteed to be the same. Therefore, the connectivity of `fes2` will in fact remain the same.
