Iteratively tighten bounds on water model variables. By default, the function uses the PWLRD relaxation for performing bound tightening.

# Example

The function can be invoked as follows:

```
gurobi = JuMP.optimizer_with_attributes(Gurobi.Optimizer)
solve_obbt_owf!("examples/data/epanet/van_zyl.inp", gurobi)
```

# Keyword Arguments

  * `model_type`: relaxation to use for performing bound tightening.
  * `max_iter`: maximum number of bound tightening iterations to perform.
  * `time_limit`: maximum amount of time (seconds) for the bound tightening algorithm.
  * `upper_bound`: can be used to specify a local feasible solution objective for the problem.
  * `upper_bound_constraint`: boolean option that can be used to add an additional  constraint to reduce the search space of each of the bound tightening  solves. This cannot be set to `true` without specifying an upper bound.
  * `use_relaxed_network`: boolean option that specifies whether or not to use a relaxed,  snapshot, dispatchable version of the origin multinetwork problem for bound tightening.
