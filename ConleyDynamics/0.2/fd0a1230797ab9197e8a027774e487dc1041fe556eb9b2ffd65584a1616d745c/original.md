```
persistent_homology(lc::LefschetzComplex, filtration::Vector{Int})
```

Complete the persistent homology of a Lefschetz complex filtration over the field associated with the Lefschetz complex boundary matrix.

The function returns the two values

  * `phsingles::Vector{Vector{Int}}`
  * `phpairs::Vector{Vector{Tuple{Int,Int}}}`

It assumes that the order given by the filtration values is admissible, i.e., the permuted boundary matrix is strictly upper triangular. The function returns the starting filtration values for infinite length persistence intervals in `phsingles`, and the birth- and death-filtration values for finite length persistence intervals in `phpairs`.
