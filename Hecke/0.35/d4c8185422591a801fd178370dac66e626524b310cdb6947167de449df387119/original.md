```
locally_free_class_group_with_disc_log(O::AlgAssAbsOrd; check::Bool = true)
  -> FinGenAbGroup, DiscLogLocallyFreeClassGroup
```

Given a group ring $O$, this function returns the locally free class group of $O$ and map from the set of ideals of $O$ to this group. As the function only works for group rings, it is tested whether `A = algebra(O)` is of type `GroupAlgebra` and whether `O == order(A, basis(A))`. These tests can be disabled by setting `check = false`.
