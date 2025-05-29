```
XPRSgetduals(prob, duals, first, last)::status, duals
```

Used to obtain the dual values associated with the incumbent solution during or after optimization of a continuous problem with XPRSoptimize, XPRSlpoptimize or `XPRSnlpoptimize`.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `duals::Union{XPRSallocatable,AbstractVector{Float64}}`: Double pointer where the value of the dual variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First row in the dual solution.
  * `last::Integer`: Last row in the dual solution.

# Return values

  * `status::Int32`: Information about the dual solution returned.
  * `duals::AbstractVector{Float64}`: Double pointer where the value of the dual variables will be returned.

See also the documentation of the correponding function [XPRSgetduals](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetduals.html) in the C API.
