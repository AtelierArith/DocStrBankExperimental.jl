```
XPRSgetcols(prob, start, rowind, rowcoef, maxcoefs, first, last)::start, rowind, rowcoef, ncoefs
```

Returns the nonzeros in the constraint matrix for the columns in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `start::AbstractVector{Int32}`: Integer array which will be filled with the indices indicating the starting offsets in the `rowind` and `rowcoef` arrays for each requested column.
  * `rowind::AbstractVector{Int32}`: Integer array of length `maxcoefs` which will be filled with the row indices of the nonzero coefficents for each column.
  * `rowcoef::AbstractVector{Float64}`: Double array of length `maxcoefs` which will be filled with the nonzero coefficient values.
  * `maxcoefs::Integer`: The size of the `rowind` and `rowcoef` arrays.
  * `first::Integer`: First column in the range.
  * `last::Integer`: Last column in the range.

# Return values

  * `start::AbstractVector{Int32}`: Integer array which will be filled with the indices indicating the starting offsets in the `rowind` and `rowcoef` arrays for each requested column.
  * `rowind::AbstractVector{Int32}`: Integer array of length `maxcoefs` which will be filled with the row indices of the nonzero coefficents for each column.
  * `rowcoef::AbstractVector{Float64}`: Double array of length `maxcoefs` which will be filled with the nonzero coefficient values.
  * `ncoefs::Int32`: Pointer to an integer where the number of nonzero coefficients in the selected columns will be returned.

See also the documentation of the correponding function [XPRSgetcols](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcols.html) in the C API.
