```
XPRSscale(prob, rowscale, colscale)::prob
```

Re-scales the current matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rowscale::AbstractVector{Integer}`: Integer array of size ROWS containing the powers of `2` with which to scale the rows, or `nothing` if not required.
  * `colscale::AbstractVector{Integer}`: Integer array of size COLS containing the powers of `2` with which to scale the columns, or `nothing` if not required.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSscale](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSscale.html) in the C API.
