```
XPRSaddrows64(prob, nrows, ncoefs, rowtype, rhs, rng, start, colind, rowcoef)::prob
```

Adds rows to the optimizer matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: Number of new rows.
  * `ncoefs::Integer`: Number of new nonzeros in the added rows.
  * `rowtype::AbstractVector{Cchar}`: Character array of length nrows containing the row types: Lindicates a `<=` row; Gindicates `>=` row; Eindicates an = row.
  * `rhs::AbstractVector{Number}`: Double array of length `nrows` containing the right hand side elements.
  * `rng::AbstractVector{Number}`: Double array of length `nrows` containing the row range elements.
  * `start::AbstractVector{Integer}`: Integer array of length `nrows` containing the offsets in the `colind` and `rowcoef` arrays of the start of the elements for each row.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncoefs` containing the (contiguous) column indices for the elements in each row.
  * `rowcoef::AbstractVector{Number}`: Double array of length `ncoefs` containing the (contiguous) element values.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddrows64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddrows64.html) in the C API.
