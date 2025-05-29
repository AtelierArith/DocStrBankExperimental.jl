```
XPRSchgmqobj64(prob, ncoefs, objqcol1, objqcol2, objqcoef)::prob
```

Used to change multiple quadratic coefficients in the objective function.

If any of the coefficients does not exist already, new coefficients will be added to the objective function.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncoefs::Integer`: The number of coefficients to change.
  * `objqcol1::AbstractVector{Integer}`: Integer array of size `ncol` containing the column index of the first variable in each quadratic term.
  * `objqcol2::AbstractVector{Integer}`: Integer array of size `ncol` containing the column index of the second variable in each quadratic term.
  * `objqcoef::AbstractVector{Number}`: New values for the coefficients.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgmqobj64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgmqobj64.html) in the C API.
