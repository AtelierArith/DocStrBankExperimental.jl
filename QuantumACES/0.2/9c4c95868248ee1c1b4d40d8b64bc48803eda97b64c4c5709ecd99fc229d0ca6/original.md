```
eig_to_pair_idx(d::Design, eigenvalue_idx::Integer)
eig_to_pair_idx(d::Design, eigenvalue_indices::Vector{Int})
```

Returns the `(tuple_idx, mapping_idx)` pair of indices for each eigenvalue index `eigenvalue_idx` corresponding to the design `d`.
