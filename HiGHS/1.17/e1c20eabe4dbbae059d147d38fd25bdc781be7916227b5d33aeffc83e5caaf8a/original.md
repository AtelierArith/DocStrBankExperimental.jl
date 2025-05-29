```
Highs_getBasisTransposeSolve(highs, rhs, solution_vector, solution_nz, solution_index)
```

Compute ${x}=B^{-T}{b}$ for a given vector ${b}$.

See [`Highs_getBasicVariables`](@ref) for a description of the $B$ matrix.

The arrays `solution_vector` and `solution_index` must have an allocated length of [num_row]. However, check `solution_num_nz` to see how many non-zero elements are actually stored.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `rhs`: The right-hand side vector $b$
  * `solution_vector`: An array of length [num_row] in which to store the values of the non-zero elements.
  * `solution_num_nz`: The number of non-zeros in the solution.
  * `solution_index`: An array of length [num_row] in which to store the indices of the non-zero elements.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
