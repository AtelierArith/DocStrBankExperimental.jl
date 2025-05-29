```
XPRSgetrhs(prob, rhs, first, last)::rhs
```

Returns the right hand side elements for the rows in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rhs::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length `last-first+1` where the right hand side elements are to be placed. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First row in the range.
  * `last::Integer`: Last row in the range.

# Return value

  * `rhs::AbstractVector{Float64}`: Double array of length `last-first+1` where the right hand side elements are to be placed.

See also the documentation of the correponding function [XPRSgetrhs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrhs.html) in the C API.
