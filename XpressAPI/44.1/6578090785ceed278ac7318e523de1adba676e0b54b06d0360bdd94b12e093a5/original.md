```
XPRSgetcutmap(prob, ncuts, cutind, cutmap)::cutmap
```

Used to return in which rows a list of cuts are currently loaded into the Optimizer.

This is useful for example to retrieve the duals associated with active cuts.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncuts::Integer`: Number of cuts in the cutind array.
  * `cutind::AbstractVector{Ptr{Cvoid}}`: Pointer array to the cuts for which the row index is requested.
  * `cutmap::Union{XPRSallocatable,AbstractVector{Int32}}`: Integer array of length `ncuts`, where the row indices are returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return value

  * `cutmap::AbstractVector{Int32}`: Integer array of length `ncuts`, where the row indices are returned.

See also the documentation of the correponding function [XPRSgetcutmap](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcutmap.html) in the C API.
