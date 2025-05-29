```
XPRSgetqrowcoeff(prob, row, rowqcol1, rowqcol2)::rowqcoef
```

Returns a single quadratic constraint coefficient corresponding to the variable pair (`rowqcol1`, `rowqcol2`) of the Hessian of a given constraint.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: The quadratic row where the coefficient is to be looked up.
  * `rowqcol1::Integer`: Column index for the first variable in the quadratic term.
  * `rowqcol2::Integer`: Column index for the second variable in the quadratic term.

# Return value

  * `rowqcoef::Float64`: Pointer to a double value where the objective function coefficient is to be placed.

See also the documentation of the correponding function [XPRSgetqrowcoeff](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqrowcoeff.html) in the C API.
