```
eig_to_pair_idx(d::Design, eigenvalue_idx::Integer)
eig_to_pair_idx(d::Design, eigenvalue_indices::Vector{Int})
```

デザイン `d` に対応する各固有値インデックス `eigenvalue_idx` のインデックスの `(tuple_idx, mapping_idx)` ペアを返します。
