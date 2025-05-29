```
update(F::LUFactor, pos::Int, newcol::SparseVector) -> (lhs, piverr)
```

Update the factorization by inserting column `newcol` at index `pos`.
