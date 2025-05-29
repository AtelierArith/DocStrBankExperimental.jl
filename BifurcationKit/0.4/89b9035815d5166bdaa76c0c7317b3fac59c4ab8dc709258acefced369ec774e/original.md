```julia
generate_ci_problem(
    pb,
    bifprob,
    sol_ode,
    period;
    cache_In,
    optimal_period
)

```

Generate a periodic orbit problem from a solution.

## Arguments

  * `pb` a `PeriodicOrbitOCollProblem` which provides basic information, like the number of time slices `M`
  * `bifprob` a bifurcation problem to provide the vector field
  * `sol` basically an `ODEProblem` or a function `t -> sol(t)`
  * `period` estimate of the period of the periodic orbit

## Output

  * returns a `PeriodicOrbitOCollProblem` and an initial guess.
