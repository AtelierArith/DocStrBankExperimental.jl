```
XPRSgetpivotorder(prob, pivotorder)::pivotorder
```

Returns the pivot order of the basic variables.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `pivotorder::Union{XPRSallocatable,AbstractVector{Int32}}`: Integer array of length ROWS where the pivot order will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return value

  * `pivotorder::AbstractVector{Int32}`: Integer array of length ROWS where the pivot order will be returned.

See also the documentation of the correponding function [XPRSgetpivotorder](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpivotorder.html) in the C API.
