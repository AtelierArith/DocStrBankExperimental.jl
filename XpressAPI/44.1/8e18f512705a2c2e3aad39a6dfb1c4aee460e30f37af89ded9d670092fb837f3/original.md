```
XPRSdelqmatrix(prob, row)::prob
```

Deletes the quadratic part of a row or of the objective function.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: Index of row from which the quadratic part is to be deleted.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelqmatrix](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelqmatrix.html) in the C API.
