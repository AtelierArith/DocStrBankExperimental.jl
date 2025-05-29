Solves the LP problem using the self-scaled solver.

# Arguments

  * `lp`: The `LPModel` instance.
  * `logging`: Level of logging detail (default: `0`).
  * `monotone`: Enforce monotonicity (default: `true`).
  * `max_time`: Maximum solving time in seconds (default: `30.0`).
  * `kwargs`: Additional keyword arguments.

# Returns

A statistics object containing the solution and status.

# Notes

  * If the solution is found but the residual norm exceeds `1e-1`, the status is set to `:infeasible`.
