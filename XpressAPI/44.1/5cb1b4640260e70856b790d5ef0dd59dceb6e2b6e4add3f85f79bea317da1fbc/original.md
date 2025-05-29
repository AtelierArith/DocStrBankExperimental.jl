```
XPRSnlpdelformulas(prob, nformulas, rowind)::prob
```

Delete nonlinear formulas from the current problem

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `nformulas::Integer`: Number of SLP nonlinear formulas to delete.
  * `rowind::AbstractVector{Integer}`: Row indices of the SLP nonlinear formulas to delete.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSnlpdelformulas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpdelformulas.html) in the C API.
