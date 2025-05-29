```
XPRSchgqrowcoeff(prob, row, rowqcol1, rowqcol2, rowqcoef)::prob
```

Changes a single quadratic coefficient in a row.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: Index of the row where the quadratic matrix is to be changed.
  * `rowqcol1::Integer`: First index of the coefficient to be changed.
  * `rowqcol2::Integer`: Second index of the coefficient to be changed.
  * `rowqcoef::Float64`: The new coefficient.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgqrowcoeff](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgqrowcoeff.html) in the C API.
