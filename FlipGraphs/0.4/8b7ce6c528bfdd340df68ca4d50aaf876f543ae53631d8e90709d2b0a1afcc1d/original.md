```
mcKay_vertices(D::DeltaComplex; , A_deltacomplex::Matrix{<:Integer}, point_perm::Vector{<:Integer}) :: Vector{Vector{Int32}}
```

Apply a version of McKay's canonical graph labeling algorithm in order to determine all possible permutations  of the `TriFace`s which give a canonical isomorphism class representant.

Return a vector of permutation vectors `p` such that `TriFace` 1 becomes `TriFace` `p[1]`, `TriFace` 2 becomes `TriFace` `p[2]`, ...
If `only_one=true`, the algorithm stops after finding one valid permutation.

The vectors `point_perm` determins how the points of `D` are implied to have been renamed, without actually having been changed.
