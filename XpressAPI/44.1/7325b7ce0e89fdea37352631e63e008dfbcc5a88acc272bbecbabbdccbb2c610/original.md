```
XPRSchgmcoef64(prob, ncoefs, rowind, colind, rowcoef)::prob
```

Used to change multiple coefficients in the matrix.

If any coefficient does not already exist, it will be added to the matrix. If many coefficients are being added to a row of the matrix, it may be more efficient to delete the old row of the matrix and add a new one.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncoefs::Integer`: Number of new coefficients.
  * `rowind::AbstractVector{Integer}`: Integer array of length `ncoefs` containing the row indices of the coefficients to be changed.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncoefs` containing the column indices of the coefficients to be changed.
  * `rowcoef::AbstractVector{Number}`: Double array of length `ncoefs` containing the new coefficient values.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgmcoef64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgmcoef64.html) in the C API.
