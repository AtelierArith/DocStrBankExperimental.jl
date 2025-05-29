```
XPRSaddmipsol(prob, len, solval, colind, name)::prob
```

Adds a new feasible, infeasible or partial MIP solution for the problem to the Optimizer.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `len::Integer`: Number of columns for which a value is provided.
  * `solval::AbstractVector{Number}`: Double array of length `length` containing solution values.
  * `colind::AbstractVector{Integer}`: Optional integer array of length `length` containing the column indices for the solution values provided in `solval`.
  * `name::Union{Nothing,AbstractString}`: An optional name to associate with the solution.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddmipsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddmipsol.html) in the C API.
