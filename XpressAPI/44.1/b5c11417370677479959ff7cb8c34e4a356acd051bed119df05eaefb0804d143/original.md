```
XPRSbndsa(prob, ncols, colind, lblower, lbupper, ublower, ubupper)::lblower, lbupper, ublower, ubupper
```

Returns upper and lower sensitivity ranges for specified variables' lower and upper bounds.

If the bounds are varied within these ranges the current basis remains optimal and feasible.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncols::Integer`: Number of variables whose sensitivity is sought.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the indices of the columns whose bounds' ranges are required.
  * `lblower::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the variable lower bound lower range values are to be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `lbupper::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the variable lower bound upper range values are to be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `ublower::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the variable upper bound lower range values are to be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `ubupper::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the variable upper bound upper range values are to be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `lblower::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the variable lower bound lower range values are to be returned.
  * `lbupper::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the variable lower bound upper range values are to be returned.
  * `ublower::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the variable upper bound lower range values are to be returned.
  * `ubupper::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ncols` where the variable upper bound upper range values are to be returned.

See also the documentation of the correponding function [XPRSbndsa](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSbndsa.html) in the C API.
