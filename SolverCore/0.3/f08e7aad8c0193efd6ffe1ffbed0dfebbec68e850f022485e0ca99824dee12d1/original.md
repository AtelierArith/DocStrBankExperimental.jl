```
GenericExecutionStats(nlp; ...)
GenericExecutionStats{T, S, V, Tsp}(;...)
```

A GenericExecutionStats is a struct for storing the output information of solvers. It contains the following fields:

  * `status`: Indicates the output of the solver. Use `show_statuses()` for the full list;
  * `solution`: The final approximation returned by the solver (default: an uninitialized vector like `nlp.meta.x0`);
  * `objective`: The objective value at `solution` (default: `Inf`);
  * `dual_feas`: The dual feasibility norm at `solution` (default: `Inf`);
  * `primal_feas`: The primal feasibility norm at `solution` (default: `0.0` if unconstrained, `Inf` otherwise);
  * `multipliers`: The Lagrange multipliers wrt to the constraints (default: an uninitialized vector like `nlp.meta.y0`);
  * `multipliers_L`: The Lagrange multipliers wrt to the lower bounds on the variables (default: an uninitialized vector like `nlp.meta.x0` if there are bounds, or a zero-length vector if not);
  * `multipliers_U`: The Lagrange multipliers wrt to the upper bounds on the variables (default: an uninitialized vector like `nlp.meta.x0` if there are bounds, or a zero-length vector if not);
  * `iter`: The number of iterations computed by the solver (default: `-1`);
  * `elapsed_time`: The elapsed time computed by the solver (default: `Inf`);
  * `solver_specific::Dict{Symbol,Any}`: A solver specific dictionary.

The constructor preallocates storage for the fields above. Special storage may be used for `multipliers_L` and `multipliers_U` by passing them to the constructor. For instance, if a problem has few bound constraints, those multipliers could be held in sparse vectors.

The following fields indicate whether the information above has been updated and is reliable:

  * `solution_reliable`
  * `objective_reliable`
  * `residuals_reliable` (for `dual_feas` and `primal_feas`)
  * `multipliers_reliable` (for `multipliers`)
  * `bounds_multipliers_reliable` (for `multipliers_L` and `multipliers_U`)
  * `iter_reliable`
  * `time_reliable`
  * `solver_specific_reliable`.

Setting fields using one of the methods `set_solution!()`, `set_objective!()`, etc., also marks the field value as reliable.

The `reset!()` method marks all fields as unreliable.

`nlp` is highly recommended to set default optional fields. If it is not provided, the function `reset!(stats, nlp)` should be called before `solve!`.

All other variables can be input as keyword arguments.

Notice that `GenericExecutionStats` does not compute anything, it simply stores.
