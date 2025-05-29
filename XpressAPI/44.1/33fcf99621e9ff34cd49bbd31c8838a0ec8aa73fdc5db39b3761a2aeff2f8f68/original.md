```
XPRSaddpwlcons64(prob, npwls, npoints, colind, resultant, start, xval, yval)::prob
```

Adds one or more piecewise linear constraints to the problem.

Each piecewise linear constraint `y = f(x)` consists of an (input) column x, a (different) resultant (output column) y and a piecewise linear function f. The piecewise linear function f is described by at least two breakpoints, which are given as combinations of x- and y-values. Discontinuous piecewise linear functions are supported, in this case both the left and right limit at a given point need to be entered as breakpoints. To differentiate between left and right limit, the breakpoints need to be given as a list with non-decreasing x-values.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `npwls::Integer`: The number of piecewise linear constraints to add.
  * `npoints::Integer`: The total number of breakpoints of all piecewise linear constraints that should be added.
  * `colind::AbstractVector{Integer}`: Integer array of length `npwls` containing the indices of the input variables x of the piecewise linear functions.
  * `resultant::AbstractVector{Integer}`: Integer array of length `npwls` containing the indices of the output variables y of the piecewise linear functions.
  * `start::AbstractVector{Integer}`: Integer array of length `npwls` containing the start index of each piecewise linear constraint in the `xval` and `yval` arrays.
  * `xval::AbstractVector{Number}`: Double array of length `npoints` containing the x-values of the breakpoints.
  * `yval::AbstractVector{Number}`: Double array of length `npoints` containing the y-values of the breakpoints.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddpwlcons64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddpwlcons64.html) in the C API.
