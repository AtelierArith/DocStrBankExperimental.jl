```
XPRSestimaterowdualranges(prob, nrows, rowind, iterlim, mindual, maxdual)::mindual, maxdual
```

Performs a dual side range sensitivity analysis, i.e. calculates estimates for the possible ranges for dual values.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: The number of rows to analyze.
  * `rowind::AbstractVector{Integer}`: Row indices to analyze.
  * `iterlim::Integer`: Effort limit expressed as simplex iterations per row.
  * `mindual::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Estimated lower bounds on the possible dual ranges. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `maxdual::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Estimated upper bounds on the possible dual ranges. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `mindual::Union{Nothing,AbstractVector{Float64}}`: Estimated lower bounds on the possible dual ranges.
  * `maxdual::Union{Nothing,AbstractVector{Float64}}`: Estimated upper bounds on the possible dual ranges.

See also the documentation of the correponding function [XPRSestimaterowdualranges](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSestimaterowdualranges.html) in the C API.
