Iteratively tighten bounds on voltage magnitude and phase-angle difference variables.

The function can be invoked on any convex relaxation which explicitly has these variables. By default, the function uses the QC relaxation for performing bound-tightening. Interested readers are refered to the paper "Strengthening Convex Relaxations with Bound Tightening for Power Network Optimization".

# Example

The function can be invoked as follows:

```
data, stats = solve_obbt_opf!("matpower/case3.m", Ipopt.Optimizer)
```

`data` contains the parsed network data with tightened bounds. `stats` contains information output from the bounds-tightening algorithm. It looks roughly like

```
Dict{String,Any} with 19 entries:
  "initial_relaxation_objective" => 5817.91
  "vm_range_init"                => 0.6
  "final_relaxation_objective"   => 5901.96
  "avg_vm_range_init"            => 0.2
  "final_rel_gap_from_ub"        => NaN
  "run_time"                     => 0.832232
  "model_type"            => AbstractPowerModel
  "avg_td_range_final"           => 0.436166
  "initial_rel_gap_from_ub"      => Inf
  "sim_parallel_run_time"        => 1.13342
  "upper_bound"                  => Inf
  "vm_range_final"               => 0.6
  "vad_sign_determined"          => 2
  "avg_td_range_init"            => 1.0472
  "avg_vm_range_final"           => 0.2
  "iteration_count"              => 5
  "td_range_init"                => 3.14159
  "td_range_final"               => 1.3085
```

# Keyword Arguments

  * `model_type`: relaxation to use for performing bound-tightening.   Currently, it supports any relaxation that has explicit voltage magnitude   and phase-angle difference variables.
  * `max_iter`: maximum number of bound-tightening iterations to perform.
  * `time_limit`: maximum amount of time (sec) for the bound-tightening algorithm.
  * `upper_bound`: can be used to specify a local feasible solution objective for   the AC Optimal Power Flow problem.
  * `upper_bound_constraint`: boolean option that can be used to add an additional   constraint to reduce the search space of each of the bound-tightening   solves. This cannot be set to `true` without specifying an upper bound.
  * `rel_gap_tol`: tolerance used to terminate the algorithm when the objective   value of the relaxation is close to the upper bound specified using the   `upper_bound` keyword.
  * `min_bound_width`: domain beyond which bound-tightening is not performed.
  * `termination`: Bound-tightening algorithm terminates if the improvement in   the average or maximum bound improvement, specified using either the   `termination = :avg` or the `termination = :max` option, is less than   `improvement_tol`.
  * `precision`: number of decimal digits to round the tightened bounds to.
