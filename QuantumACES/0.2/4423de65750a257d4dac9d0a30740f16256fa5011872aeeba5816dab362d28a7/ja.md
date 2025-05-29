```
pair_to_eig_idx(d::Design, pair_idx::Tuple{Int, Int})
pair_to_eig_idx(d::Design, pair_indices::Vector{Tuple{Int, Int}})
```

デザイン `d` に対応するペアインデックス `(tuple_idx, mapping_idx)` に対応する固有値インデックス `eigenvalue_idx` を返します。
