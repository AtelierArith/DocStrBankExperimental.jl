```
XPRSloadlpsol(prob, x, slack, duals, djs)::status
```

Loads an LP solution for the problem into the Optimizer.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `x::AbstractVector{Number}`: Optional: Double array of length COLS (for the original problem and not the presolve problem) containing the values of the variables.
  * `slack::AbstractVector{Number}`: Optional: double array of length ROWS containing the values of slack variables.
  * `duals::AbstractVector{Number}`: Optional: double array of length ROWS containing the values of dual variables.
  * `djs::AbstractVector{Number}`: Optional: double array of length COLS containing the values of reduced costs.

# Return value

  * `status::Int32`: Pointer to an `int` where the status will be returned.

See also the documentation of the correponding function [XPRSloadlpsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadlpsol.html) in the C API.
