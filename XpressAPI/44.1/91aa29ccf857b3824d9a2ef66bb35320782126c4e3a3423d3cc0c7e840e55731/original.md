```
XPRSgetredcosts(prob, djs, first, last)::status, djs
```

Used to obtain the reduced costs associated with the incumbent solution during or after optimization of a continuous problem with XPRSoptimize, XPRSlpoptimize or `XPRSnlpoptimize`.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `djs::Union{XPRSallocatable,AbstractVector{Float64}}`: Double pointer where the reduced costs for the variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First column in the reduced costs.
  * `last::Integer`: Last column in the reduced costs.

# Return values

  * `status::Int32`: Information about the reduced costs returned.
  * `djs::AbstractVector{Float64}`: Double pointer where the reduced costs for the variables will be returned.

See also the documentation of the correponding function [XPRSgetredcosts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetredcosts.html) in the C API.
