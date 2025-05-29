```
Highs_getBasicVariables(highs, basic_variables)
```

Get the indices of the rows and columns that make up the basis matrix $B$ of a basic feasible solution.

Non-negative entries are indices of columns, and negative entries are `-row\_index - 1`. For example, `{1, -1}` would be the second column and first row.

The order of these rows and columns is important for calls to the functions:

  * [`Highs_getBasisInverseRow`](@ref) - [`Highs_getBasisInverseCol`](@ref) - [`Highs_getBasisSolve`](@ref) - [`Highs_getBasisTransposeSolve`](@ref) - [`Highs_getReducedRow`](@ref) - [`Highs_getReducedColumn`](@ref)

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `basic_variables`: An array of size [num_rows], filled with the indices of the basic variables.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
