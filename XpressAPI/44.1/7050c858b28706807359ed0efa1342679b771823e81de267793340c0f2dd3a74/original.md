```
XPRScalcreducedcosts(prob, duals, solution, djs)::djs
```

Calculates the reduced cost values for a given (row) dual solution.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `duals::AbstractVector{Number}`: Double array of length ROWS that holds the dual solution to calculate the reduced costs for.
  * `solution::AbstractVector{Number}`: Optional double array of length COLS that holds the primal solution.
  * `djs::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length COLS in which the calculated reduced costs are returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return value

  * `djs::AbstractVector{Float64}`: Double array of length COLS in which the calculated reduced costs are returned.

See also the documentation of the correponding function [XPRScalcreducedcosts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcreducedcosts.html) in the C API.
