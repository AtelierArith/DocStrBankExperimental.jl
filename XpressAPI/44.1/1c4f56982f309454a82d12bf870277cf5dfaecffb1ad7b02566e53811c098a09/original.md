```
XPRSloadbasis(prob, rowstat, colstat)::prob
```

Loads a basis from the user's areas.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rowstat::AbstractVector{Integer}`: Integer array of length ROWS containing the basis status of the slack, surplus or artificial variable associated with each row.
  * `colstat::AbstractVector{Integer}`: Integer array of length COLS containing the basis status of each of the columns in the constraint matrix.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSloadbasis](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadbasis.html) in the C API.
