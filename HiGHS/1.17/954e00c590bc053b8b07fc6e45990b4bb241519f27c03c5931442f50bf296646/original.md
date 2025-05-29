```
Highs_getModel(highs, a_format, q_format, num_col, num_row, num_nz, hessian_num_nz, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, q_start, q_index, q_value, integrality)
```

Get the data from a HiGHS model.

The input arguments have the same meaning (in a different order) to those used in [`Highs_passModel`](@ref).

Note that all arrays must be pre-allocated to the correct size before calling [`Highs_getModel`](@ref). Use the following query methods to check the appropriate size: - [`Highs_getNumCol`](@ref) - [`Highs_getNumRow`](@ref) - [`Highs_getNumNz`](@ref) - [`Highs_getHessianNumNz`](@ref)

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
