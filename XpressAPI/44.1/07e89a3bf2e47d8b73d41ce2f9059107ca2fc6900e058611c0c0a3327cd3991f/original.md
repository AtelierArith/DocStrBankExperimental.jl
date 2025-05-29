```
XPRSslpevaluatecoef(prob, row, col)::value
```

Evaluate a coefficient using the current values of the variables

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: Integer index of the row.
  * `col::Integer`: Integer index of the column.

# Return value

  * `value::Float64`: Address of a double precision value to receive the result of the calculation.

See also the documentation of the correponding function [XPRSslpevaluatecoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpevaluatecoef.html) in the C API.
