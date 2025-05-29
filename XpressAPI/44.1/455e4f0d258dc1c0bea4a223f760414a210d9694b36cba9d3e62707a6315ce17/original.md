```
XPRSgetpresolvemap(prob, rowmap, colmap)::rowmap, colmap
```

Returns the mapping of the row and column numbers from the presolve problem back to the original problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rowmap::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length ROWS where the row maps will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colmap::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length COLS where the column maps will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `rowmap::Union{Nothing,AbstractVector{Int32}}`: Integer array of length ROWS where the row maps will be returned.
  * `colmap::Union{Nothing,AbstractVector{Int32}}`: Integer array of length COLS where the column maps will be returned.

See also the documentation of the correponding function [XPRSgetpresolvemap](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpresolvemap.html) in the C API.
