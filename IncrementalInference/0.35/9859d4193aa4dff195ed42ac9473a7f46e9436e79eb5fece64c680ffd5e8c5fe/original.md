```julia
getEliminationOrder(dfg; ordering, solvable, constraints)

```

Determine the variable ordering used to construct both the Bayes Net and Bayes/Junction/Elimination tree.

Notes

  * Heuristic method – equivalent to QR or Cholesky.
  * Are using Blas `QR` function to extract variable ordering.
  * **NOT USING SUITE SPARSE** – which would requires commercial license.
  * For now `A::Array{<:Number,2}` as a dense matrix.
  * Columns of `A` are system variables, rows are factors (without differentiating between partial or full factor).
  * default is to use `solvable=1` and ignore factors and variables that might be used for dead reckoning or similar.

Future

  * TODO: `A` should be sparse data structure (when we exceed 10'000 var dims)
  * TODO: Incidence matrix is rectagular and adjacency is the square.
