```
XPRSgetrhsrange(prob, rng, first, last)::rng
```

Returns the right hand side range values for the rows in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rng::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length `last-first+1` where the right hand side range values are to be placed. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First row in the range.
  * `last::Integer`: Last row in the range.

# Return value

  * `rng::AbstractVector{Float64}`: Double array of length `last-first+1` where the right hand side range values are to be placed.

See also the documentation of the correponding function [XPRSgetrhsrange](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrhsrange.html) in the C API.
