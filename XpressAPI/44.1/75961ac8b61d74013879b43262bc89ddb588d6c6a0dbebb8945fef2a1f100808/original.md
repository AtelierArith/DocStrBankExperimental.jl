```
XPRSbasiscondition(prob)::cond, scaledcond
```

**Deprecated**Please use the XPRSbasisstability function instead.

Calculates the condition number of the current basis after solving the LP relaxation.

# Arguments

  * `prob::XPRSprob`: The current problem.

# Return values

  * `cond::Float64`: The returned condition number of the current basis.
  * `scaledcond::Float64`: The returned condition number of the current basis for the scaled problem.

See also the documentation of the correponding function [XPRSbasiscondition](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSbasiscondition.html) in the C API.
