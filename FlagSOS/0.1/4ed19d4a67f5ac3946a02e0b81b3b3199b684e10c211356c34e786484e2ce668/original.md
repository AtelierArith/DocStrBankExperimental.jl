```
glue(F::PartiallyLabeledFlag{T}, G::PartiallyLabeledFlag{T}, p::Vector{Int})
```

Glues together the two partially labeled Flags `F` and `G`, after applying the permutation `p` to the vertices of `F`. `p` may be a permutation involving more than `size(F)` vertices, but should send the labeled part of `F` to the labeled part of `G`, without permuting indices there.
