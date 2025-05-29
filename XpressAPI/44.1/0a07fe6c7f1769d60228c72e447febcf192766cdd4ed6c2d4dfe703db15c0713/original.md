```
XPRSchgobj(prob, ncols, colind, objcoef)::prob
```

Used to change the objective function coefficients.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncols::Integer`: Number of objective function coefficient elements to change.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the indices of the columns whose objective coefficients will change.
  * `objcoef::AbstractVector{Number}`: Double array of length `ncols` giving the new objective function coefficients.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgobj.html) in the C API.
