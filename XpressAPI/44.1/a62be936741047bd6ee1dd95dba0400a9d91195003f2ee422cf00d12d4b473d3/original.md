```
XPRSgetcallbackduals(prob, duals, first, last)::available, duals
```

Returns the dual values from the solution associated with the current callback.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `duals::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length `last-first+1` where the values of the dual variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First row whose dual value to return.
  * `last::Integer`: Last row whose dual value to return.

# Return values

  * `available::Int32`: This variable will be set to 1 if a dual solution is available.
  * `duals::AbstractVector{Float64}`: Double array of length `last-first+1` where the values of the dual variables will be returned.

See also the documentation of the correponding function [XPRSgetcallbackduals](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbackduals.html) in the C API.
