```
XPRSslpdelcoefs(prob, ncoefs, rowind, colind)::prob
```

Delete coefficients from the current problem.

For a simpler version of this function see XSLPdelformulas.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `ncoefs::Integer`: Number of SLP coefficients to delete.
  * `rowind::AbstractVector{Integer}`: Row indices of the SLP coefficients to delete.
  * `colind::AbstractVector{Integer}`: Column indices of the SLP coefficients to delete.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSslpdelcoefs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpdelcoefs.html) in the C API.
