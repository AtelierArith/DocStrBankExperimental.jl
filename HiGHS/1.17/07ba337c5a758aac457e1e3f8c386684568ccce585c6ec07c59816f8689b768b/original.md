```
Highs_mipCall(num_col, num_row, num_nz, a_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, integrality, col_value, row_value, model_status)
```

Formulate and solve a mixed-integer linear program using HiGHS.

The signature of this method is identical to [`Highs_lpCall`](@ref), except that it has an additional `integrality` argument, and that it is missing the `col_dual`, `row_dual`, `col_basis_status` and `row_basis_status` arguments.

### Parameters

  * `integrality`: An array of length [num_col], containing a `kHighsVarType` constant for each column.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
