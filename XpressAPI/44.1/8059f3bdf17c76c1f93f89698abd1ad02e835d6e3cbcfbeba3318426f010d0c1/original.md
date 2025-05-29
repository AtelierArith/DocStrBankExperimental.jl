```
XPRSgetsolution(prob, x, first, last)::status, x
```

Used to obtain the incumbent solution during or after optimization with XPRSoptimize, XPRSmipoptimize, XPRSlpoptimize or `XPRSnlpoptimize`.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `x::Union{XPRSallocatable,AbstractVector{Float64}}`: Double pointer where the value of the primal variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First column in the solution.
  * `last::Integer`: Last column in the solution.

# Return values

  * `status::Int32`: Information about the solution returned.
  * `x::AbstractVector{Float64}`: Double pointer where the value of the primal variables will be returned.

See also the documentation of the correponding function [XPRSgetsolution](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetsolution.html) in the C API.
