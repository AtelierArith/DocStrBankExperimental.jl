```
mcKay(g::TriangulatedPolygon) :: Vector{Vector{<:Integer}}
```

Apply *McKay's canonical graph labeling algorithm* to determine all possible permutations  of the vertices, which give a canonical isomorphism class representant.

Return a list of all possible canonical point-relabeling permutations `p` such that the i-th point should be relabeled as the `p[i]`-th point
