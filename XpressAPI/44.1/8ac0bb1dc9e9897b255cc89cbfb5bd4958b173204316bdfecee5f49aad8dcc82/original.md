```
XPRSchgbounds(prob, nbounds, colind, bndtype, bndval)::prob
```

Used to change the bounds on columns in the matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nbounds::Integer`: Number of bounds to change.
  * `colind::AbstractVector{Integer}`: Integer array of size `nbounds` containing the indices of the columns on which the bounds will change.
  * `bndtype::AbstractVector{Cchar}`: Character array of length `nbounds` indicating the type of bound to change: Uindicates change the upper bound; Lindicates change the lower bound; Bindicates change both bounds, i.e. fix the column.
  * `bndval::AbstractVector{Number}`: Double array of length `nbounds` giving the new bound values.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgbounds](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgbounds.html) in the C API.
