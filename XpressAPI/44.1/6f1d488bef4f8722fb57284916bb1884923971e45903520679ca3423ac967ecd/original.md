```
XPRSloaddelayedrows(prob, nrows, rowind)::prob
```

Specifies that a set of rows in the matrix will be treated as delayed rows during a tree search.

These are rows that must be satisfied for any integer solution, but will not be loaded into the active set of constraints until required.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: The number of delayed rows.
  * `rowind::AbstractVector{Integer}`: An array of row indices to treat as delayed rows.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSloaddelayedrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloaddelayedrows.html) in the C API.
