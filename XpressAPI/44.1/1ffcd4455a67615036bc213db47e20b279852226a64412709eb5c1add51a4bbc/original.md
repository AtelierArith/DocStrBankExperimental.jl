```
XPRSaddqmatrix(prob, row, ncoefs, rowqcol1, rowqcol2, rowqcoef)::prob
```

Adds a new quadratic matrix into a row defined by triplets.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: Index of the row where the quadratic matrix is to be added.
  * `ncoefs::Integer`: Number of triplets used to define the quadratic matrix.
  * `rowqcol1::AbstractVector{Integer}`: First index in the triplets.
  * `rowqcol2::AbstractVector{Integer}`: Second index in the triplets.
  * `rowqcoef::AbstractVector{Number}`: Coefficients in the triplets.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddqmatrix](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddqmatrix.html) in the C API.
