```
glue(F::PartiallyColoredFlag{T}, G::PartiallyColoredFlag{T}, p::Vector{Int})
```

Glues together the two partially labeled Flags `F` and `G`, after applying the permutation `p` to the vertices of `F`. `p` may be a permutation involving more than `size(F)` vertices, but should vertices with the same colors to vertices with the same colors.
