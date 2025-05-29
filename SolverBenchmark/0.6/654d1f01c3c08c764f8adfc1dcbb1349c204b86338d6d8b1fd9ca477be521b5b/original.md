```
performance_profile(stats, cost, args...; b = PlotsBackend(), kwargs...)
```

Produce a performance profile comparing solvers in `stats` using the `cost` function.

Inputs:

  * `stats::Dict{Symbol,DataFrame}`: pairs of `:solver => df`;
  * `cost::Function`: cost function applyed to each `df`. Should return a vector with the cost of solving the problem at each row;

      * 0 cost is not allowed;
      * If the solver did not solve the problem, return Inf or a negative number.
  * `b::BenchmarkProfiles.AbstractBackend` : backend used for the plot.

Examples of cost functions:

  * `cost(df) = df.elapsed_time`: Simple `elapsed_time` cost. Assumes the solver solved the problem.
  * `cost(df) = (df.status .!= :first_order) * Inf + df.elapsed_time`: Takes into consideration the status of the solver.
