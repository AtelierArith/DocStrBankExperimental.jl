```
XPRSaddcuts64(prob, ncuts, cuttype, rowtype, rhs, start, colind, cutcoef)::prob
```

Adds cuts directly to the matrix at the current node.

The cuts will automatically be added to the cut pool. Cuts added to a node will automatically be inherited on any descendant node, unless explicitly deleted with a call to XPRSdelcuts.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncuts::Integer`: Number of cuts to add.
  * `cuttype::AbstractVector{Integer}`: Integer array of length `ncuts` containing the user assigned cut types.
  * `rowtype::AbstractVector{Cchar}`: Character array of length `ncuts` containing the row types: Lindicates a `<=` row; Gindicates a `>=` row; Eindicates an = row.
  * `rhs::AbstractVector{Number}`: Double array of length `ncuts` containing the right hand side elements for the cuts.
  * `start::AbstractVector{Integer}`: Integer array containing offset into the `colind` and `cutcoef` arrays indicating the start of each cut.
  * `colind::AbstractVector{Integer}`: Integer array of length `start[ncuts]` containing the column indices in the cuts.
  * `cutcoef::AbstractVector{Number}`: Double array of length `start[ncuts]` containing the matrix values for the cuts.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddcuts64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddcuts64.html) in the C API.
