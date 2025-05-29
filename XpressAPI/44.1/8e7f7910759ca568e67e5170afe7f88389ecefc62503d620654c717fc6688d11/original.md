```
XPRSnlpgetformularows(prob, rowind)::nformulas, rowind
```

Retrieve the list of positions of the nonlinear formulas in the problem

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `rowind::AbstractVector{Int32}`: Integer array used for returning the row positions of the nonlinear formulas. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return values

  * `nformulas::Int32`: Integer used to return the total number of nonlinear formulas in the problem.
  * `rowind::AbstractVector{Int32}`: Integer array used for returning the row positions of the nonlinear formulas.

See also the documentation of the correponding function [XPRSnlpgetformularows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpgetformularows.html) in the C API.
