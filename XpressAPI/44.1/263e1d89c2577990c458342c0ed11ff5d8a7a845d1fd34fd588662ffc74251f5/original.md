```
XPRSaddcols(prob, ncols, ncoefs, objcoef, start, rowind, rowcoef, lb, ub)::prob
```

Adds columns to the optimizer matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncols::Integer`: Number of new columns.
  * `ncoefs::Integer`: Number of new nonzeros in the added columns.
  * `objcoef::AbstractVector{Number}`: Double array of length `ncols` containing the objective function coefficients of the new columns.
  * `start::AbstractVector{Integer}`: Integer array of length `ncols` containing the offsets in the `rowind` and `rowcoef` arrays of the start of the elements for each column.
  * `rowind::AbstractVector{Integer}`: Integer array of length `ncoefs` containing the row indices for the elements in each column.
  * `rowcoef::AbstractVector{Number}`: Double array of length `ncoefs` containing the element values.
  * `lb::AbstractVector{Number}`: Double array of length `ncols` containing the lower bounds on the added columns.
  * `ub::AbstractVector{Number}`: Double array of length `ncols` containing the upper bounds on the added columns.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddcols](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddcols.html) in the C API.
