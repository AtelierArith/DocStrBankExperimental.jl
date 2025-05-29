```
XPRSchgglblimit(prob, ncols, colind, limit)::prob
```

Used to change semi-continuous or semi-integer lower bounds, or upper limits on partial integers.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncols::Integer`: Number of column limits to change.
  * `colind::AbstractVector{Integer}`: Integer array of size `ncols` containing the indices of the semi-continuous, semi-integer or partial integer columns that should have their limits changed.
  * `limit::AbstractVector{Number}`: Double array of length `ncols` giving the new limit values.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgglblimit](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgglblimit.html) in the C API.
