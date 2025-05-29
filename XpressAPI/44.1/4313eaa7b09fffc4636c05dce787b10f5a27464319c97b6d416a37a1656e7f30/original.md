```
XPRSdelcpcuts(prob, cuttype, interp, ncuts, cutind)::prob
```

During the branch and bound search, cuts are stored in the cut pool to be applied at descendant nodes.

These cuts may be removed from a given node using XPRSdelcuts, but if this is to be applied in a large number of cases, it may be preferable to remove the cut completely from the cut pool. This is achieved using `XPRSdelcpcuts`.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `cuttype::Integer`: User defined cut type to match against.
  * `interp::Integer`: Way in which the cut `cuttype` is interpreted: -1match all cut types; 1treat cut types as numbers; 2treat cut types as bit maps - delete if any bit matches any bit set in `cuttype`; 3treat cut types as bit maps - delete if all bits match those set in `cuttype`.
  * `ncuts::Integer`: The number of cuts to delete.
  * `cutind::AbstractVector{Ptr{Cvoid}}`: Array containing pointers to the cuts which are to be deleted.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelcpcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelcpcuts.html) in the C API.
