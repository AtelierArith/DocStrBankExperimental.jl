```
mcKay_vertices(D::DeltaComplex; kwargs..) :: Vector{Vector{Int32}}
```

Apply a version of McKay's canonical graph labeling algorithm in order to determine all possible permutations  of the `TriFace`s which give a canonical isomorphism class representant.

Return a vector of permutation vectors `p` such that `TriFace` 1 becomes `TriFace` `p[1]`, `TriFace` 2 becomes `TriFace` `p[2]`, ...
If `only_one=true`, the algorithm stops after finding one valid permutation.

# Arguments

  * `only_one :: Bool = false`, If set to true, the algorithm will stop after finding a single valid permutation.
  * A_deltacomplex :: Matrix{<:Integer} = Matrix{Int32}(adjacency*matrix*deltacomplex(D)). If provided, the algorithm will use the adjacency matrix of the `DeltaComplex` `D`. If not, the algorithm would have to compute it itself.
