```
Highs_lpCall(num_col, num_row, num_nz, a_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, col_value, col_dual, row_value, row_dual, col_basis_status, row_basis_status, model_status)
```

Formulate and solve a linear program using HiGHS.

### Parameters

  * `num_col`: The number of columns.
  * `num_row`: The number of rows.
  * `num_nz`: The number of nonzeros in the constraint matrix.
  * `a_format`: The format of the constraint matrix as a `kHighsMatrixFormat` constant.
  * `sense`: The optimization sense as a `kHighsObjSense` constant.
  * `offset`: The objective constant.
  * `col_cost`: An array of length [num_col] with the column costs.
  * `col_lower`: An array of length [num_col] with the column lower bounds.
  * `col_upper`: An array of length [num_col] with the column upper bounds.
  * `row_lower`: An array of length [num_row] with the row lower bounds.
  * `row_upper`: An array of length [num_row] with the row upper bounds.
  * `a_start`: The constraint matrix is provided to HiGHS in compressed sparse column form (if `a_format` is `kHighsMatrixFormatColwise`, otherwise compressed sparse row form). The sparse matrix consists of three arrays, `a_start`, `a_index`, and `a_value`. `a_start` is an array of length [num_col] containing the starting index of each column in `a_index`. If `a_format` is `kHighsMatrixFormatRowwise` the array is of length [num_row] corresponding to each row.
  * `a_index`: An array of length [num_nz] with indices of matrix entries.
  * `a_value`: An array of length [num_nz] with values of matrix entries.
  * `col_value`: An array of length [num_col], to be filled with the primal column solution.
  * `col_dual`: An array of length [num_col], to be filled with the dual column solution.
  * `row_value`: An array of length [num_row], to be filled with the primal row solution.
  * `row_dual`: An array of length [num_row], to be filled with the dual row solution.
  * `col_basis_status`: An array of length [num_col], to be filled with the basis status of the columns in the form of a `kHighsBasisStatus` constant.
  * `row_basis_status`: An array of length [num_row], to be filled with the basis status of the rows in the form of a `kHighsBasisStatus` constant.
  * `model_status`: The location in which to place the termination status of the model after the solve in the form of a `kHighsModelStatus` constant.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
