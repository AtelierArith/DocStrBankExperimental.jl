```
XPRSpostsolvesol(prob, prex, origx)::origx
```

Postsolves a primal solution formulated in the presolved space into the corresponding solution formulated in the original space.

The problem itself is unchanged.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `prex::AbstractVector{Number}`: Double array of length COLS with the values of the primal variables in the presolved space.
  * `origx::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length ORIGINALCOLS where the values of the primal variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return value

  * `origx::AbstractVector{Float64}`: Double array of length ORIGINALCOLS where the values of the primal variables will be returned.

See also the documentation of the correponding function [XPRSpostsolvesol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSpostsolvesol.html) in the C API.
