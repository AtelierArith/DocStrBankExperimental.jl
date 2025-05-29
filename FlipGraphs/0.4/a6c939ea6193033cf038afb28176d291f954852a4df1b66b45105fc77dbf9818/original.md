```
mcKay_edges(D::DeltaComplex; kwargs..) :: Vector{Vector{Int32}}
```

Apply McKay's canonical graph labeling algorithm in order to determine all possible permutations  of the `DualEdge`s which give a canonical isomorphism class representant.

Return a vector of permutation vectors `p` such that `DualEdge` 1 becomes `DualEdge` `p[1]`, `DualEdge` 2 becomes `DualEdge` `p[2]`, ...


# Arguments

  * `only_one :: Bool = false`, If set to true, the algorithm will stop after finding a single valid permutation.
