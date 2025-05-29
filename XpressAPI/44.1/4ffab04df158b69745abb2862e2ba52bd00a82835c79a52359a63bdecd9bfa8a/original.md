```
XPRSdelcuts(prob, basis, cuttype, interp, delta, ncuts, cutind)::prob
```

Deletes cuts from the matrix at the current node.

Cuts from the parent node which have been automatically restored may be deleted as well as cuts added to the current node using XPRSaddcuts or XPRSloadcuts. The cuts to be deleted can be specified in a number of ways. If a cut is ruled out by any one of the criteria it will not be deleted.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `basis::Integer`: Ensures the basis will be valid if set to `1`.
  * `cuttype::Integer`: User defined type of the cut to be deleted.
  * `interp::Integer`: Way in which the cut `cuttype` is interpreted: -1match all cut types; 1treat cut types as numbers; 2treat cut types as bit maps - delete if any bit matches any bit set in `cuttype`; 3treat cut types as bit maps - delete if all bits match those set in `cuttype`.
  * `delta::Float64`: Only delete cuts with an absolute slack value greater than `delta`.
  * `ncuts::Integer`: Number of cuts to drop if a list of cuts is provided.
  * `cutind::AbstractVector{Ptr{Cvoid}}`: Array containing pointers to the cuts which are to be deleted.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelcuts.html) in the C API.
