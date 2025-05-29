```
XPRSgetqrows(prob, rowind)::nrows, rowind
```

Returns the list indices of the rows that have quadratic coefficients.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rowind::Union{XPRSallocatable,AbstractVector{Int32}}`: Array of length `*nrows` used to return the indices of rows with quadratic coefficients in them. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return values

  * `nrows::Int32`: Used to return the number of quadratic constraints in the matrix.
  * `rowind::AbstractVector{Int32}`: Array of length `*nrows` used to return the indices of rows with quadratic coefficients in them.

See also the documentation of the correponding function [XPRSgetqrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqrows.html) in the C API.
