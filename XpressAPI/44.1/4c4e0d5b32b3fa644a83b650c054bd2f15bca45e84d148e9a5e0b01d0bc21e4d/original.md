```
XPRSdelgencons(prob, ncons, conind)::prob
```

Delete general constraints from a problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncons::Integer`: Number of general constraints to delete.
  * `conind::AbstractVector{Integer}`: An integer array of length `ncons` containing the general constraints to delete.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelgencons](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelgencons.html) in the C API.
