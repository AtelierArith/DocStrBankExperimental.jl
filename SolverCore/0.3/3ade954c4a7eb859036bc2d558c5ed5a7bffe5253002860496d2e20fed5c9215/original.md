get_status(nlp, kwargs...)

Return the output of the solver based on the information in the keyword arguments. Use `show_statuses()` for the full list.

The keyword arguments may contain:

  * `elapsed_time::Float64 = 0.0`: current elapsed time (default: `0.0`);
  * `iter::Integer = 0`: current number of iterations (default: `0`);
  * `optimal::Bool = false`: `true` if the problem reached an optimal solution (default: `false`);
  * `small_residual::Bool = false`: `true` if the nonlinear least squares problem reached a solution with small residual (default: `false`);
  * `infeasible::Bool = false`: `true` if the problem is infeasible (default: `false`);
  * `parameter_too_large::Bool = false`: `true` if the parameters are loo large (default: `false`);
  * `unbounded::Bool = false`: `true` if the problem is unbounded (default: `false`);
  * `stalled::Bool = false`: `true` if the algorithm is stalling (default: `false`);
  * `max_eval::Integer`: limit on the number of evaluations defined by `eval_fun` (default: `typemax(Int)`);
  * `max_time::Float64 = Inf`: limit on the time (default: `Inf`);
  * `max_iter::Integer`: limit on the number of iterations (default: `typemax(Int)`).
