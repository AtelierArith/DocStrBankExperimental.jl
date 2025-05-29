```
XPRSnlpcalcslacks(prob, solution, slack)::slack
```

Calculate the slack values for the provided solution in the non-linear problem

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `solution::AbstractVector{Number}`: The solution for which the slacks are requested for.
  * `slack::Union{XPRSallocatable,AbstractVector{Float64}}`: Vector of length NROWS to return the slack in. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return value

  * `slack::AbstractVector{Float64}`: Vector of length NROWS to return the slack in.

See also the documentation of the correponding function [XPRSnlpcalcslacks](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpcalcslacks.html) in the C API.
