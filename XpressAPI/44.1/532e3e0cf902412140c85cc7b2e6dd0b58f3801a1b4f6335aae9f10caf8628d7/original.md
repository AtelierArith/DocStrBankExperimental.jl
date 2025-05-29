```
XPRSgetpresolvesol(prob, x, slack, duals, djs)::x, slack, duals, djs
```

Returns the solution for the presolved problem from memory.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length COLS where the values of the primal variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length ROWS where the values of the slack variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ROWS` where the values of the dual variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `COLS` where the reduced cost for each variable will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `x::Union{Nothing,AbstractVector{Float64}}`: Double array of length COLS where the values of the primal variables will be returned.
  * `slack::Union{Nothing,AbstractVector{Float64}}`: Double array of length ROWS where the values of the slack variables will be returned.
  * `duals::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ROWS` where the values of the dual variables will be returned.
  * `djs::Union{Nothing,AbstractVector{Float64}}`: Double array of length `COLS` where the reduced cost for each variable will be returned.

See also the documentation of the correponding function [XPRSgetpresolvesol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpresolvesol.html) in the C API.
