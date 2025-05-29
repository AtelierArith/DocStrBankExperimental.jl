```
solve(ivp::IVP{<:AbstractContinuousSystem}, tspan, alg; kwargs...)
```

Solves the initial-value problem defined by `ivp` over the time span `tspan`, using the algorithm `alg`. If no algorithm is given, a default algorithm is chosen.

### Input

  * `ivp`   – initial-value problem
  * `tspan` – time span for this initial-value problem
  * `alg`   – reachability algorithm

Additional options are passed as arguments or keyword arguments; see the notes below for details. See the online documentation for examples.

### Output

The solution of a reachability problem, as an instance of a `ReachSolution`.

### Notes

  * Use the `alg`, `algorithm` or `opC` keyword arguments to specify the algorithm to solve the initial-value problem. Algorithm-specific options should be passed to the algorithm constructor as well.
  * Use the `tspan` keyword argument to specify the time span; it can be:

      * a tuple,
      * an interval, or
      * a vector with two components.
  * Use the `T` keyword argument to specify the time horizon; the initial time is then assumed to be zero.
  * Use the `static` keyword argument to force conversion to static arrays in the algorithm (should be supported by the algorithm).
  * Use the `NSTEPS` keyword argument to specify the number of discrete steps solved in the set-based recurrence.
  * Use the `threading` option to use multi-threading parallelism. This option applies for initial-value problems whose initial condition is a vector of sets.
