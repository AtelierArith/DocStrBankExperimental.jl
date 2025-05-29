```
Highs_passLp(highs, num_col, num_row, num_nz, a_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value)
```

Pass a linear program (LP) to HiGHS in a single function call.

The signature of this function is identical to [`Highs_passModel`](@ref), without the arguments for passing the Hessian matrix of a quadratic program and the integrality vector.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
