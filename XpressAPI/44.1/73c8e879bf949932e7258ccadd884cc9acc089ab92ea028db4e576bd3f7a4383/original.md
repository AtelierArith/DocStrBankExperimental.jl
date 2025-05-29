```
XPRSloadmodelcuts(prob, nrows, rowind)::prob
```

Specifies that a set of rows in the matrix will be treated as model cuts.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: The number of model cuts.
  * `rowind::AbstractVector{Integer}`: An array of row indices to be treated as cuts.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSloadmodelcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadmodelcuts.html) in the C API.
