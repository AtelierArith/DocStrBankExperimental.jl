```
XPRSgetpresolvebasis(prob, rowstat, colstat)::rowstat, colstat
```

Returns the current basis from memory into the user's data areas.

If the problem is presolved, the presolved basis will be returned. Otherwise the original basis will be returned.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rowstat::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length ROWS to the basis status of the stack, surplus or artificial variable associated with each row. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colstat::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length COLS to hold the basis status of the columns in the constraint matrix. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `rowstat::Union{Nothing,AbstractVector{Int32}}`: Integer array of length ROWS to the basis status of the stack, surplus or artificial variable associated with each row.
  * `colstat::Union{Nothing,AbstractVector{Int32}}`: Integer array of length COLS to hold the basis status of the columns in the constraint matrix.

See also the documentation of the correponding function [XPRSgetpresolvebasis](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpresolvebasis.html) in the C API.
