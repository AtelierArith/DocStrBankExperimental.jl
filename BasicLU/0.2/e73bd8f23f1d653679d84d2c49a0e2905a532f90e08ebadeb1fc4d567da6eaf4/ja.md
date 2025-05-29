```
update(F::LUFactor, pos::Int, newcol::SparseVector) -> (lhs, piverr)
```

因子分解を更新し、インデックス `pos` に列 `newcol` を挿入します。
