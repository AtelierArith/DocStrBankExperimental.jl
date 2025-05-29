```
XPRSchgrhs(prob, nrows, rowind, rhs)::prob
```

Used to change righthand side values of the problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: Number of right hand side values to change.
  * `rowind::AbstractVector{Integer}`: Integer array of length `nrows` containing the indices of the rows on which the right hand side values will change.
  * `rhs::AbstractVector{Number}`: Double array of length `nrows` giving the right hand side values.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgrhs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgrhs.html) in the C API.
