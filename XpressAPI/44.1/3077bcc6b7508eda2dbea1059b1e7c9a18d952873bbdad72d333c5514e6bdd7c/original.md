```
XPRSchgqobj(prob, objqcol1, objqcol2, objqcoef)::prob
```

Used to change a single quadratic coefficient in the objective function corresponding to the variable pair `(objqcol1,objqcol2)` of the Hessian matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objqcol1::Integer`: Column index for the first variable in the quadratic term.
  * `objqcol2::Integer`: Column index for the second variable in the quadratic term.
  * `objqcoef::Float64`: New value for the coefficient in the quadratic Hessian matrix.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgqobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgqobj.html) in the C API.
