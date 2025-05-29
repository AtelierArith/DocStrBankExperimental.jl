```
XPRSchgobjn(prob, objidx, ncols, colind, objcoef)::prob
```

Modifies one or more coefficients of an objective function in a multi-objective problem.

If the objective already exists, any coefficients not present in the `colind` and `objcoef` arrays will unchanged. If the objective does not exist, it will be added to the problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objidx::Integer`: Index of the objective function to add or modify.
  * `ncols::Integer`: Number of objective function coefficient elements to change.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the indices of the columns whose objective coefficients will change.
  * `objcoef::AbstractVector{Number}`: Double array of length `ncols` giving the new objective function coefficients.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgobjn](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgobjn.html) in the C API.
