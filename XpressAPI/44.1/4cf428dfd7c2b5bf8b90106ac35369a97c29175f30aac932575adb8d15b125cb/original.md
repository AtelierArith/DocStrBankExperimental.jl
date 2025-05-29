```
XPRSgetcallbackpresolvesolution(prob, x, first, last)::available, x
```

Returns the solution to the presolved problem associated with the current callback.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `x::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length `last-first+1` where the values of the primal variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First column in the solution to return.
  * `last::Integer`: Last column in the solution to return.

# Return values

  * `available::Int32`: This variable will be set to 1 if a solution is available.
  * `x::AbstractVector{Float64}`: Double array of length `last-first+1` where the values of the primal variables will be returned.

See also the documentation of the correponding function [XPRSgetcallbackpresolvesolution](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbackpresolvesolution.html) in the C API.
