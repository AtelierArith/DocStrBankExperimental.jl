```
XPRSgetqobj(prob, objqcol1, objqcol2)::objqcoef
```

Returns a single quadratic objective function coefficient corresponding to the variable pair `(objqcol1, objqcol2)` of the Hessian matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objqcol1::Integer`: Column index for the first variable in the quadratic term.
  * `objqcol2::Integer`: Column index for the second variable in the quadratic term.

# Return value

  * `objqcoef::Float64`: Pointer to a double value where the objective function coefficient is to be placed.

See also the documentation of the correponding function [XPRSgetqobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqobj.html) in the C API.
