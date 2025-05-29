```
Highs_qpCall(num_col, num_row, num_nz, q_num_nz, a_format, q_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, q_start, q_index, q_value, col_value, col_dual, row_value, row_dual, col_basis_status, row_basis_status, model_status)
```

Formulate and solve a quadratic program using HiGHS.

The signature of this method is identical to [`Highs_lpCall`](@ref), except that it has additional arguments for specifying the Hessian matrix.

### Parameters

  * `q_num_nz`: The number of nonzeros in the Hessian matrix.
  * `q_format`: The format of the Hessian matrix in the form of a `kHighsHessianStatus` constant. If q_num_nz > 0, this must be `kHighsHessianFormatTriangular`.
  * `q_start`: The Hessian matrix is provided to HiGHS as the lower triangular component in compressed sparse column form (or, equivalently, as the upper triangular component in compressed sparse row form). The sparse matrix consists of three arrays, `q_start`, `q_index`, and `q_value`. `q_start` is an array of length [num_col].
  * `q_index`: An array of length [q_num_nz] with indices of matrix entries.
  * `q_value`: An array of length [q_num_nz] with values of matrix entries.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
