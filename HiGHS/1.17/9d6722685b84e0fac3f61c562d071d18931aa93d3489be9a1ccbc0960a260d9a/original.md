```
Highs_passHessian(highs, dim, num_nz, format, start, index, value)
```

Set the Hessian matrix for a quadratic objective.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `dim`: The dimension of the Hessian matrix. Should be [num_col].
  * `num_nz`: The number of non-zero elements in the Hessian matrix.
  * `format`: The format of the Hessian matrix as a `kHighsHessianFormat` constant. This must be `kHighsHessianFormatTriangular`.
  * `start`: The Hessian matrix is provided to HiGHS as the lower triangular component in compressed sparse column form (or, equivalently, as the upper triangular component in compressed sparse row form), using `q_start`, `q_index`, and `q_value`.The Hessian matrix is provided to HiGHS as the lower triangular component in compressed sparse column form. The sparse matrix consists of three arrays, `start`, `index`, and `value`. `start` is an array of length [num_col] containing the starting index of each column in `index`.
  * `index`: An array of length [num_nz] with indices of matrix entries.
  * `value`: An array of length [num_nz] with values of matrix entries.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
