```
glue(F::InducedFlag{T}, G::InducedFlag{T}, p::Vector{Int})
```

Glues together the two induced Flags `F` and `G`, after applying the permutation `p` to the vertices of `F`. `p` may be a permutation involving more than `size(F)` vertices. Since these Flags describe induced densities, the result is a linear combination of every possible combination of "unknown" edges between the added vertices from eachothers perspectives (or equivalent). If the common part is different, they are orthogonal to each other and thus return an empty Vector.
