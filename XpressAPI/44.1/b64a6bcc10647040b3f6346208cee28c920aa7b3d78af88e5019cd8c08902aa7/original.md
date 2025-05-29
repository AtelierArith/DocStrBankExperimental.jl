```
XPRSobjsa(prob, ncols, colind, lower, upper)::lower, upper
```

Returns upper and lower sensitivity ranges for specified objective function coefficients.

If the objective coefficients are varied within these ranges the current basis remains optimal and the reduced costs remain valid.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncols::Integer`: Number of objective function coefficients whose sensitivity is sought.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the indices of the columns whose objective function coefficients sensitivity ranges are required.
  * `lower::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the objective function lower range values are to be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `upper::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the objective function upper range values are to be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `lower::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the objective function lower range values are to be returned.
  * `upper::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the objective function upper range values are to be returned.

See also the documentation of the correponding function [XPRSobjsa](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSobjsa.html) in the C API.
