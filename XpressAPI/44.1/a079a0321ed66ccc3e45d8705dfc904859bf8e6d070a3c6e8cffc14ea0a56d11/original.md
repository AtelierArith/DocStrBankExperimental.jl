```
XPRSgetcoef(prob, row, col)::coef
```

Returns a single coefficient in the constraint matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: Row of the constraint matrix.
  * `col::Integer`: Column of the constraint matrix.

# Return value

  * `coef::Float64`: Pointer to a double where the coefficient will be returned.

See also the documentation of the correponding function [XPRSgetcoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcoef.html) in the C API.
