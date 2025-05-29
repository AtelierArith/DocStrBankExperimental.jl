```
XPRSslpgetcoefs(prob, rowind, colind)::ncoefs, rowind, colind
```

Retrieve the list of positions of the nonlinear coefficients in the problem.

For a simpler version of this function see XSLPgetformularows.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `rowind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array used for returning the row positions of the coefficients. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array used for returning the column positions of the coefficients. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `ncoefs::Int32`: Integer used to return the total number of nonlinear coefficients in the problem.
  * `rowind::Union{Nothing,AbstractVector{Int32}}`: Integer array used for returning the row positions of the coefficients.
  * `colind::Union{Nothing,AbstractVector{Int32}}`: Integer array used for returning the column positions of the coefficients.

See also the documentation of the correponding function [XPRSslpgetcoefs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetcoefs.html) in the C API.
