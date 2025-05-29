```
XPRSgetinfeas(prob, x, slack, duals, djs)::nprimalcols, nprimalrows, ndualrows, ndualcols, x, slack, duals, djs
```

Returns a list of infeasible primal and dual variables.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `nprimalcols` where the primal infeasible variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `nprimalrows` where the primal infeasible rows will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `ndualrows` where the dual infeasible rows will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `ndualcols` where the dual infeasible variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `nprimalcols::Int32`: Pointer to an integer where the number of primal infeasible variables is returned.
  * `nprimalrows::Int32`: Pointer to an integer where the number of primal infeasible rows is returned.
  * `ndualrows::Int32`: Pointer to an integer where the number of dual infeasible rows is returned.
  * `ndualcols::Int32`: Pointer to an integer where the number of dual infeasible variables is returned.
  * `x::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `nprimalcols` where the primal infeasible variables will be returned.
  * `slack::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `nprimalrows` where the primal infeasible rows will be returned.
  * `duals::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `ndualrows` where the dual infeasible rows will be returned.
  * `djs::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `ndualcols` where the dual infeasible variables will be returned.

See also the documentation of the correponding function [XPRSgetinfeas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetinfeas.html) in the C API.
