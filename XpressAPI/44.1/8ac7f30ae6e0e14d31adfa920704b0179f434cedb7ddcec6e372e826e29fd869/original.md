```
XPRSdelindicators(prob, first, last)::prob
```

Delete indicator constraints.

This turns the specified rows into normal rows (not controlled by indicator variables).

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `first::Integer`: First row in the range.
  * `last::Integer`: Last row in the range (inclusive).

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelindicators](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelindicators.html) in the C API.
