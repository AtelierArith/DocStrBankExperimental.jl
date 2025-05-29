```
XPRSstorecuts(prob, ncuts, nodups, cuttype, rowtype, rhs, start, cutind, colind, cutcoef)::cutind
```

Stores cuts into the cut pool, but does not apply them to the current node.

These cuts must be explicitly loaded into the matrix using XPRSloadcuts before they become active.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncuts::Integer`: Number of cuts to add.
  * `nodups::Integer`: 0do not exclude duplicates from the cut pool; 1duplicates are to be excluded from the cut pool; 2duplicates are to be excluded from the cut pool, ignoring cut type.
  * `cuttype::AbstractVector{Integer}`: Integer array of length `ncuts` containing the cut types.
  * `rowtype::AbstractVector{Cchar}`: Character array of length `ncuts` containing the row types: Lindicates a `<=` row; Eindicates an = row; Gindicates a `>=` row.
  * `rhs::AbstractVector{Number}`: Double array of length `ncuts` containing the right hand side elements for the cuts.
  * `start::AbstractVector{Integer}`: Integer array containing offsets into the `colind` and `dmtval` arrays indicating the start of each cut.
  * `cutind::Union{XPRSallocatable,AbstractVector{Ptr{Cvoid}}}`: Array of length `ncuts` where the pointers to the cuts will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `colind::AbstractVector{Integer}`: Integer array of length `start[ncuts]` containing the column indices in the cuts.
  * `cutcoef::AbstractVector{Number}`: Double array of length `start[ncuts]` containing the matrix values for the cuts.

# Return value

  * `cutind::AbstractVector{Ptr{Cvoid}}`: Array of length `ncuts` where the pointers to the cuts will be returned.

See also the documentation of the correponding function [XPRSstorecuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSstorecuts.html) in the C API.
