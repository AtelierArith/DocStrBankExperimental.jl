```
XPRSbtran(prob, vec)::vec
```

Post-multiplies a (row) vector provided by the user by the inverse of the current basis.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `vec::AbstractVector{Float64}`: Double array of length ROWS containing the values by which the basis inverse is to be multiplied.

# Return value

  * `vec::AbstractVector{Float64}`: Double array of length ROWS containing the values by which the basis inverse is to be multiplied.

See also the documentation of the correponding function [XPRSbtran](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSbtran.html) in the C API.
