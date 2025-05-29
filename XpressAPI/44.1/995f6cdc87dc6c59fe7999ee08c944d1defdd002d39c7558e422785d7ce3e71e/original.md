```
XPRSgetqrowqmatrix(prob, row, start, colind, rowqcoef, maxcoefs, first, last)::start, colind, rowqcoef, ncoefs
```

Returns the nonzeros in a quadratic constraint coefficients matrix for the columns in a given range.

To achieve maximum efficiency, `XPRSgetqrowqmatrix` returns the lower triangular part of this matrix only.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: Index of the row for which the quadratic coefficients are to be returned.
  * `start::AbstractVector{Int32}`: Integer array which will be filled with indices indicating the starting offsets in the `colind` and `rowqcoef` arrays for each requested column.
  * `colind::AbstractVector{Int32}`: Integer array of length maxcoefs which will be filled with the column indices of the nonzero elements in the lower triangular part of Q.
  * `rowqcoef::AbstractVector{Float64}`: Double array of length maxcoefs which will be filled with the nonzero element values.
  * `maxcoefs::Integer`: Number of elements to be saved in colind and rowqcoef.
  * `first::Integer`: First column in the range.
  * `last::Integer`: Last column in the range.

# Return values

  * `start::AbstractVector{Int32}`: Integer array which will be filled with indices indicating the starting offsets in the `colind` and `rowqcoef` arrays for each requested column.
  * `colind::AbstractVector{Int32}`: Integer array of length maxcoefs which will be filled with the column indices of the nonzero elements in the lower triangular part of Q.
  * `rowqcoef::AbstractVector{Float64}`: Double array of length maxcoefs which will be filled with the nonzero element values.
  * `ncoefs::Int32`: Pointer to the integer where the number of nonzero elements in the queried columns will be returned.

See also the documentation of the correponding function [XPRSgetqrowqmatrix](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqrowqmatrix.html) in the C API.
