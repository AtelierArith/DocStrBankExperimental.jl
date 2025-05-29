```
XPRSgetslacks(prob, slacks, first, last)::status, slacks
```

Used to obtain the slack values associated with the incumbent solution during or after optimization with XPRSoptimize, XPRSmipoptimize, XPRSlpoptimize or `XPRSnlpoptimize`.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `slacks::Union{XPRSallocatable,AbstractVector{Float64}}`: Double pointer where the value of the slack variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First row in the slacks.
  * `last::Integer`: Last row in the slacks.

# Return values

  * `status::Int32`: Information about the slacks returned.
  * `slacks::AbstractVector{Float64}`: Double pointer where the value of the slack variables will be returned.

See also the documentation of the correponding function [XPRSgetslacks](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetslacks.html) in the C API.
