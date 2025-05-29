```
XPRSchgcoef(prob, row, col, coef)::prob
```

Used to change a single coefficient in the matrix.

If the coefficient does not already exist, a new coefficient will be added to the matrix. If many coefficients are being added to a row of the matrix, it may be more efficient to delete the old row of the matrix and add a new row.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: Row index for the coefficient.
  * `col::Integer`: Column index for the coefficient.
  * `coef::Float64`: New value for the coefficient.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgcoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgcoef.html) in the C API.
