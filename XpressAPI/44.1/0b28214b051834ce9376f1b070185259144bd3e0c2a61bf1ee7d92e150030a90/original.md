```
XPRSpresolverow(prob, rowtype, norigcoefs, origcolind, origrowcoef, origrhs, maxcoefs, colind, rowcoef)::ncoefs, colind, rowcoef, rhs, status
```

Presolves a row formulated in terms of the original variables such that it can be added to a presolved matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rowtype::Integer`: The type of the row: Lindicates a `<=` row; Gindicates a `>=` row.
  * `norigcoefs::Integer`: Number of elements in the `origcolind` and `origrowcoef` arrays.
  * `origcolind::AbstractVector{Integer}`: Integer array of length `norigcoefs` containing the column indices of the row to presolve.
  * `origrowcoef::AbstractVector{Number}`: Double array of length `norigcoefs` containing the non-zero coefficients of the row to presolve.
  * `origrhs::Float64`: The right-hand side constant of the row to presolve.
  * `maxcoefs::Integer`: Maximum number of elements to return in the `colind` and `rowcoef` arrays.
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the column indices of the presolved row. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `rowcoef::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array which will be filled with the coefficients of the presolved row. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `ncoefs::Int32`: Pointer to the integer where the number of elements in the `colind` and `rowcoef` arrays will be returned.
  * `colind::Union{Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the column indices of the presolved row.
  * `rowcoef::Union{Nothing,AbstractVector{Float64}}`: Double array which will be filled with the coefficients of the presolved row.
  * `rhs::Float64`: Pointer to the double where the presolved right-hand side will be returned.
  * `status::Int32`: Status of the presolved row: -3Failed to presolve the row due to presolve dual reductions; -2Failed to presolve the row due to presolve duplicate column reductions; -1Failed to presolve the row due to an error.

See also the documentation of the correponding function [XPRSpresolverow](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSpresolverow.html) in the C API.
