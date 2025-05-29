```
XPRSchgrhsrange(prob, nrows, rowind, rng)::prob
```

Used to change the range for a row of the problem matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: Number of range elements to change.
  * `rowind::AbstractVector{Integer}`: Integer array of length `nrows` containing the indices of the rows on which the range elements will change.
  * `rng::AbstractVector{Number}`: Double array of length `nrows` giving the range values.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgrhsrange](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgrhsrange.html) in the C API.
