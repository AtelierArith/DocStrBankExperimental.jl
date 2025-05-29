```
XPRSftran(prob, vec)::vec
```

Pre-multiplies a (column) vector provided by the user by the inverse of the current matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `vec::AbstractVector{Float64}`: Double array of length ROWS containing the values which are to be multiplied by the basis inverse.

# Return value

  * `vec::AbstractVector{Float64}`: Double array of length ROWS containing the values which are to be multiplied by the basis inverse.

See also the documentation of the correponding function [XPRSftran](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSftran.html) in the C API.
