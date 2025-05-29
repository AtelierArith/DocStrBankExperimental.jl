```
XPRSdelrows(prob, nrows, rowind)::prob
```

Delete rows from a matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: Number of rows to delete.
  * `rowind::AbstractVector{Integer}`: An integer array of length `nrows` containing the rows to delete.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelrows.html) in the C API.
