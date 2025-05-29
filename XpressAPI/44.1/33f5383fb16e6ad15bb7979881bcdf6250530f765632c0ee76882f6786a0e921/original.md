```
XPRSgetpwlcons(prob, colind, resultant, start, xval, yval, maxpoints, first, last)::colind, resultant, start, xval, yval, npoints
```

Returns the piecewise linear constraints `y = f(x)` in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the indices of the input variables `x`. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `resultant::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the indices of the output variables `y`. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `start::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the start indices of the different constraints in the breakpoint arrays. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `xval::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `maxpoints` which will be filled with the `x`-values of the breakpoints. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `yval::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `maxpoints` which will be filled with the `y`-values of the breakpoints. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `maxpoints::Integer`: Maximum number of breakpoints to be retrieved.
  * `first::Integer`: First piecewise linear constraint in the range.
  * `last::Integer`: Last piecewise linear constraint in the range.

# Return values

  * `colind::Union{Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the indices of the input variables `x`.
  * `resultant::Union{Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the indices of the output variables `y`.
  * `start::Union{Nothing,AbstractVector{Int32}}`: Integer array which will be filled with the start indices of the different constraints in the breakpoint arrays.
  * `xval::Union{Nothing,AbstractVector{Float64}}`: Double array of length `maxpoints` which will be filled with the `x`-values of the breakpoints.
  * `yval::Union{Nothing,AbstractVector{Float64}}`: Double array of length `maxpoints` which will be filled with the `y`-values of the breakpoints.
  * `npoints::Int32`: Pointer to return the number of breakpoints in the selected constraints.

See also the documentation of the correponding function [XPRSgetpwlcons](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpwlcons.html) in the C API.
