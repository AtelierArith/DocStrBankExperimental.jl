```
XPRScalcobjective(prob, solution)::objval
```

Calculates the objective value of a given solution.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `solution::AbstractVector{Number}`: Double array of length COLS that holds the solution.

# Return value

  * `objval::Float64`: Pointer to a double in which the calculated objective value is returned.

See also the documentation of the correponding function [XPRScalcobjective](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcobjective.html) in the C API.
