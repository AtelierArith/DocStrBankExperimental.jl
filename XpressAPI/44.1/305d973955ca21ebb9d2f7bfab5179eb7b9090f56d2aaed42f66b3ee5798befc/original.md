```
XPRSgetscaledinfeas(prob, x, slack, duals, djs)::nprimalcols, nprimalrows, ndualrows, ndualcols, x, slack, duals, djs
```

Returns a list of scaled infeasible primal and dual variables for the original problem.

If the problem is currently presolved, it is postsolved before the function returns.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `nprimalcols` where the primal infeasible variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `nprimalrows` where the primal infeasible rows will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `ndualrows` where the dual infeasible rows will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `ndualcols` where the dual infeasible variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `nprimalcols::Int32`: Number of primal infeasible variables.
  * `nprimalrows::Int32`: Number of primal infeasible rows.
  * `ndualrows::Int32`: Number of dual infeasible rows.
  * `ndualcols::Int32`: Number of dual infeasible variables.
  * `x::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `nprimalcols` where the primal infeasible variables will be returned.
  * `slack::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `nprimalrows` where the primal infeasible rows will be returned.
  * `duals::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `ndualrows` where the dual infeasible rows will be returned.
  * `djs::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `ndualcols` where the dual infeasible variables will be returned.

See also the documentation of the correponding function [XPRSgetscaledinfeas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetscaledinfeas.html) in the C API.
