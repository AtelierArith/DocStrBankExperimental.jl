```
XPRSloadcuts(prob, cuttype, interp, ncuts, cutind)::prob
```

Loads cuts from the cut pool into the matrix.

Without calling `XPRSloadcuts` the cuts will remain in the cut pool but will not be active at the node. Cuts loaded at a node remain active at all descendant nodes unless they are deleted using XPRSdelcuts.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `cuttype::Integer`: Cut type.
  * `interp::Integer`: The way in which the cut type is interpreted: -1load all cuts; 1treat cut types as numbers; 2treat cut types as bit maps - load cut if any bit matches any bit set in `cuttype`; 3treat cut types as bit maps - `0` load cut if all bits match those set in `cuttype`.
  * `ncuts::Integer`: Number of cuts to load.
  * `cutind::AbstractVector{Ptr{Cvoid}}`: Array of length `ncuts` containing pointers to the cuts to be loaded into the matrix.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSloadcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadcuts.html) in the C API.
