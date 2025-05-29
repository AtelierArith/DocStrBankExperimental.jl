```
XPRSloadmipsol(prob, x)::status
```

Loads a starting MIP solution for the problem into the Optimizer.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `x::AbstractVector{Number}`: Double array of length COLS (for the original problem and not the presolve problem) containing the values of the variables.

# Return value

  * `status::Int32`: Pointer to an `int` where the status will be returned.

See also the documentation of the correponding function [XPRSloadmipsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadmipsol.html) in the C API.
