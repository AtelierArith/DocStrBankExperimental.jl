```
mcKay_points(D::DeltaComplex; kwargs..) :: Vector{Vector{Int32}}
```

Apply a version of McKay's canonical graph labeling algorithm to determine all possible permutations  of the points which give a canonical isomorphism class representant.

Return a vector of permutation vectors `p` such that point 1 becomes point `p[1]`, point 2 becomes point `p[2]`,...

# Arguments

  * `only_one :: Bool = false`, If set to true, the algorithm will stop after finding a single valid permutation.
