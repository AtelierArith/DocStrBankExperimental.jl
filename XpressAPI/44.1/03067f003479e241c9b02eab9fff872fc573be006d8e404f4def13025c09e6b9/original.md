```
XPRSnlpvalidatevector(prob, solution)::suminf, sumscaledinf, objval
```

Validate the feasibility of constraints for a given solution

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `solution::AbstractVector{Number}`: A vector of length `XPRS_COLS` containing the solution vector to be checked.

# Return values

  * `suminf::Float64`: Pointer to double in which the sum of infeasibility will be returned.
  * `sumscaledinf::Float64`: Pointer to double in which the sum of scaled (relative) infeasibility will be returned.
  * `objval::Float64`: Pointer to double in which the net objective will be returned.

See also the documentation of the correponding function [XPRSnlpvalidatevector](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpvalidatevector.html) in the C API.
