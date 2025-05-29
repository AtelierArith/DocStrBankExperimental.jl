```
XPRSsparseftran(prob, val, ind)::val, ind, ncoefs
```

Pre-multiplies a (column) vector provided by the user by the inverse of the current matrix.

Sparse version of XPRSftran.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `val::AbstractVector{Float64}`: Double array of length ROWS containing the values which are to be multiplied by the basis inverse.
  * `ind::AbstractVector{Int32}`: Integer array of indices identifying the non-zero entries of `val`.

# Return values

  * `val::AbstractVector{Float64}`: Double array of length ROWS containing the values which are to be multiplied by the basis inverse.
  * `ind::AbstractVector{Int32}`: Integer array of indices identifying the non-zero entries of `val`.
  * `ncoefs::Int32`: Memory location where the number of non-zero entries is given.

See also the documentation of the correponding function [XPRSsparseftran](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsparseftran.html) in the C API.
