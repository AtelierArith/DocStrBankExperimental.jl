```
XPRSgetscale(prob, rowscale, colscale)::rowscale, colscale
```

Returns the the current scaling of the matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rowscale::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of size ROWS that will contain the powers of `2` with which the rows are currently scaled. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colscale::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of size COLS that will contain the powers of `2` with which the columns are currently scaled. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `rowscale::Union{Nothing,AbstractVector{Int32}}`: Integer array of size ROWS that will contain the powers of `2` with which the rows are currently scaled.
  * `colscale::Union{Nothing,AbstractVector{Int32}}`: Integer array of size COLS that will contain the powers of `2` with which the columns are currently scaled.

See also the documentation of the correponding function [XPRSgetscale](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetscale.html) in the C API.
