```
XPRSgetcpcuts(prob, rowind, ncuts, maxcoefs, cuttype, rowtype, start, colind, cutcoef, rhs)::cuttype, rowtype, start, colind, cutcoef, rhs
```

Returns cuts from the cut pool.

A list of cut pointers in the array `rowind` must be passed to the routine. The columns and elements of the cut will be returned in the regions pointed to by the `colind` and `cutcoef` parameters. The columns and elements will be stored contiguously and the starting point of each cut will be returned in the region pointed to by the `start` parameter.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rowind::AbstractVector{Ptr{Cvoid}}`: Array of length `ncuts` containing the pointers to the cuts.
  * `ncuts::Integer`: Number of cuts to be returned.
  * `maxcoefs::Integer`: Maximum number of column indices of the cuts to be returned.
  * `cuttype::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length at least `ncuts` where the cut types will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `rowtype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: Character array of length at least `ncuts` where the sense of the cuts (`L`, `G`, or `E`) will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `start::AbstractVector{Int32}`: Integer array of length at least `ncuts+1` containing the offsets into the `colind` and `cutcoef` arrays.
  * `colind::AbstractVector{Int32}`: Integer array of length `maxcoefs` where the column indices of the cuts will be returned.
  * `cutcoef::AbstractVector{Float64}`: Double array of length `maxcoefs` where the matrix values will be returned.
  * `rhs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length at least `ncuts` where the right hand side elements for the cuts will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `cuttype::Union{Nothing,AbstractVector{Int32}}`: Integer array of length at least `ncuts` where the cut types will be returned.
  * `rowtype::Union{Nothing,AbstractVector{Cchar}}`: Character array of length at least `ncuts` where the sense of the cuts (`L`, `G`, or `E`) will be returned.
  * `start::AbstractVector{Int32}`: Integer array of length at least `ncuts+1` containing the offsets into the `colind` and `cutcoef` arrays.
  * `colind::AbstractVector{Int32}`: Integer array of length `maxcoefs` where the column indices of the cuts will be returned.
  * `cutcoef::AbstractVector{Float64}`: Double array of length `maxcoefs` where the matrix values will be returned.
  * `rhs::Union{Nothing,AbstractVector{Float64}}`: Double array of length at least `ncuts` where the right hand side elements for the cuts will be returned.

See also the documentation of the correponding function [XPRSgetcpcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcpcuts.html) in the C API.
