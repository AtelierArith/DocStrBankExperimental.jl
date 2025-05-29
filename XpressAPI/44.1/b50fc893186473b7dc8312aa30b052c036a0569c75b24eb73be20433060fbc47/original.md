```
XPRSloadbranchdirs(prob, ncols, colind, dir)::prob
```

Loads directives into the current problem to specify which MIP entities the Optimizer should continue to branch on when a node solution is integer feasible.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncols::Integer`: Number of directives.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the column numbers.
  * `dir::AbstractVector{Integer}`: Integer array of length `ncols` containing either 0 or 1 for the entities given in `colind`.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSloadbranchdirs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadbranchdirs.html) in the C API.
