```
XPRSgetcallbackpresolveslacks(prob, slacks, first, last)::available, slacks
```

Returns the slack values from the solution to the presolved problem associated with the current callback.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `slacks::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length `last-first+1` where the values of the slack variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First row whose slack value to return.
  * `last::Integer`: Last row whose slack value to return.

# Return values

  * `available::Int32`: This variable will be set to 1 if a solution is available.
  * `slacks::AbstractVector{Float64}`: Double array of length `last-first+1` where the values of the slack variables will be returned.

See also the documentation of the correponding function [XPRSgetcallbackpresolveslacks](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbackpresolveslacks.html) in the C API.
