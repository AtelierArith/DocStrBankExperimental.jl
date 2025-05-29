```
XPRSdelcols(prob, ncols, colind)::prob
```

Delete columns from a matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncols::Integer`: Number of columns to delete.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the columns to delete.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelcols](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelcols.html) in the C API.
