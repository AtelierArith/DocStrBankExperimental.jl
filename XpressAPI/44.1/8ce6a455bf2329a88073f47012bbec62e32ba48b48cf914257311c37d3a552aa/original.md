```
XPRSfixmipentities(prob, options)::prob
```

Fixes all the MIP entities to the values of the last found MIP solution.

This is useful for finding the reduced costs for the continuous variables after the integer variables have been fixed to their optimal values.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `options::Integer`: Options how to fix the MIP entities. 0If all MIP entities should be rounded to the nearest discrete value in the solution before being fixed. 1If piecewise linear and general constraints should be kept in the problem with only the non-convex decisions (i.e. which part of a non-convex piecewise linear function or which variable attains a maximum) fixed.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSfixmipentities](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSfixmipentities.html) in the C API.
