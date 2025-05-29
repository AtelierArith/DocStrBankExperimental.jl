An empty `PairwiseListMatrix` can be created for a given `Type` and a number of elements `nelements`. The `diagonal` (default to `false`) can be declared as `true` to indicate that the list needs space for the diagonal elements. If `diagonal` is `false` the diagonal values are stored in a vector on the `diag` field instead of being on the list. The `diag` vector can be filled with the optional `diagonalvalue` argument (default to `0`).

```julia
PairwiseListMatrix(Int, 3)
PairwiseListMatrix(Int, 3, true)
```
