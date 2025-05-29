```
XPRSgetlpsolval(prob, col, row)::x, slack, dual, dj
```

**Deprecated**Use XPRSgetsolution or XPRSgetcallbacksolution and related functions instead.

Used to obtain a single LP solution value following optimization.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `col::Integer`: Column index of the variable for which to return the solution value.
  * `row::Integer`: Row index of the constraint for which to return the solution value.

# Return values

  * `x::Float64`: Double pointer where the value of the primal variable will be returned.
  * `slack::Float64`: Double pointer where the value of the slack variable will be returned.
  * `dual::Float64`: Double pointer where the value of the dual variable (cBTB-1) will be returned.
  * `dj::Float64`: Double pointer where the reduced costs for the variable (cT-cBTB-1A) will be returned.

See also the documentation of the correponding function [XPRSgetlpsolval](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetlpsolval.html) in the C API.
