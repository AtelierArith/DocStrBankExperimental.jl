```
pair_to_eig_idx(d::Design, pair_idx::Tuple{Int, Int})
pair_to_eig_idx(d::Design, pair_indices::Vector{Tuple{Int, Int}})
```

Returns the eigenvalue index `eigenvalue_idx` corresponding to the pair index `(tuple_idx, mapping_idx)` corresponding to the design `d`.
