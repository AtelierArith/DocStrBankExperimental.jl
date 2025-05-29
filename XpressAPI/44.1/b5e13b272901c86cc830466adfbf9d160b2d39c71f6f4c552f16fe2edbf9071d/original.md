```
XPRSgetmqobj(prob, start, colind, objqcoef, maxcoefs, first, last)::start, colind, objqcoef, ncoefs
```

Returns the nonzeros in the quadratic objective coefficients matrix for the columns in a given range.

To achieve maximum efficiency, `XPRSgetmqobj` returns the lower triangular part of this matrix only.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `start::AbstractVector{Int32}`: Integer array which will be filled with indices indicating the starting offsets in the `colind` and `objqcoef` arrays for each requested column.
  * `colind::AbstractVector{Int32}`: Integer array of length `maxcoefs` which will be filled with the column indices of the nonzero elements in the lower triangular part of `Q`.
  * `objqcoef::AbstractVector{Float64}`: Double array of length `maxcoefs` which will be filled with the nonzero element values.
  * `maxcoefs::Integer`: The maximum number of elements to be returned (size of the arrays).
  * `first::Integer`: First column in the range.
  * `last::Integer`: Last column in the range.

# Return values

  * `start::AbstractVector{Int32}`: Integer array which will be filled with indices indicating the starting offsets in the `colind` and `objqcoef` arrays for each requested column.
  * `colind::AbstractVector{Int32}`: Integer array of length `maxcoefs` which will be filled with the column indices of the nonzero elements in the lower triangular part of `Q`.
  * `objqcoef::AbstractVector{Float64}`: Double array of length `maxcoefs` which will be filled with the nonzero element values.
  * `ncoefs::Int32`: Pointer to an integer where the number of nonzero quadratic objective coefficients will be returned.

See also the documentation of the correponding function [XPRSgetmqobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmqobj.html) in the C API.
