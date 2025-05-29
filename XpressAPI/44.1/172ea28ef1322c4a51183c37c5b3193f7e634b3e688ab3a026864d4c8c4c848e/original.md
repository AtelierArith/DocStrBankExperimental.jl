```
XPRSgetmipsol(prob, x, slack)::x, slack
```

**Deprecated**Use XPRSgetsolution and XPRSgetslacks instead.

Used to obtain the solution values of the last MIP solution that was found.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length ORIGINALCOLS where the values of the primal variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length ORIGINALROWS where the values of the slack variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `x::Union{Nothing,AbstractVector{Float64}}`: Double array of length ORIGINALCOLS where the values of the primal variables will be returned.
  * `slack::Union{Nothing,AbstractVector{Float64}}`: Double array of length ORIGINALROWS where the values of the slack variables will be returned.

See also the documentation of the correponding function [XPRSgetmipsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmipsol.html) in the C API.
