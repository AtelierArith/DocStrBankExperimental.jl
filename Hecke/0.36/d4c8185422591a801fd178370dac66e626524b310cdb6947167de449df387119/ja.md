```
locally_free_class_group_with_disc_log(O::AlgAssAbsOrd; check::Bool = true)
  -> FinGenAbGroup, DiscLogLocallyFreeClassGroup
```

与えられた群環 $O$ に対して、この関数は $O$ の局所自由類群と $O$ のイデアルの集合からこの群への写像を返します。この関数は群環に対してのみ機能するため、`A = algebra(O)` が `GroupAlgebra` 型であり、かつ `O == order(A, basis(A))` であるかどうかがテストされます。これらのテストは `check = false` に設定することで無効にできます。
