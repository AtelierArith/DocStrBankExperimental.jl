```
Highs_passModel(highs, num_col, num_row, num_nz, q_num_nz, a_format, q_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, q_start, q_index, q_value, integrality)
```

Pass a model to HiGHS in a single function call. This is faster than constructing the model using [`Highs_addRow`](@ref) and [`Highs_addCol`](@ref).

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_col`: The number of columns.
  * `num_row`: The number of rows.
  * `num_nz`: The number of elements in the constraint matrix.
  * `q_num_nz`: The number of elements in the Hessian matrix.
  * `a_format`: The format of the constraint matrix to use in the form of a `kHighsMatrixFormat` constant.
  * `q_format`: The format of the Hessian matrix to use in the form of a `kHighsHessianFormat` constant.
  * `sense`: The optimization sense in the form of a `kHighsObjSense` constant.
  * `offset`: The constant term in the objective function.
  * `col_cost`: An array of length [num_col] with the objective coefficients.
  * `col_lower`: An array of length [num_col] with the lower column bounds.
  * `col_upper`: An array of length [num_col] with the upper column bounds.
  * `row_lower`: An array of length [num_row] with the upper row bounds.
  * `row_upper`: An array of length [num_row] with the upper row bounds.
  * `a_start`: The constraint matrix is provided to HiGHS in compressed sparse column form (if `a_format` is `kHighsMatrixFormatColwise`, otherwise compressed sparse row form). The sparse matrix consists of three arrays, `a_start`, `a_index`, and `a_value`. `a_start` is an array of length [num_col] containing the starting index of each column in `a_index`. If `a_format` is `kHighsMatrixFormatRowwise` the array is of length [num_row] corresponding to each row.
  * `a_index`: An array of length [num_nz] with indices of matrix entries.
  * `a_value`: An array of length [num_nz] with values of matrix entries.
  * `q_start`: The Hessian matrix is provided to HiGHS as the lower triangular component in compressed sparse column form (or, equivalently, as the upper triangular component in compressed sparse row form). The sparse matrix consists of three arrays, `q_start`, `q_index`, and `q_value`. `q_start` is an array of length [num_col]. If the model is linear, pass NULL.
  * `q_index`: An array of length [q_num_nz] with indices of matrix entries. If the model is linear, pass NULL.
  * `q_value`: An array of length [q_num_nz] with values of matrix entries. If the model is linear, pass NULL.
  * `integrality`: An array of length [num_col] containing a `kHighsVarType` constant for each column.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
