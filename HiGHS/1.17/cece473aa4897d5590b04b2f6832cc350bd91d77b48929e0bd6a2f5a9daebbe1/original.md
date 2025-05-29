```
Highs_passMip(highs, num_col, num_row, num_nz, a_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, integrality)
```

Pass a mixed-integer linear program (MILP) to HiGHS in a single function call.

The signature of function is identical to [`Highs_passModel`](@ref), without the arguments for passing the Hessian matrix of a quadratic program.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
