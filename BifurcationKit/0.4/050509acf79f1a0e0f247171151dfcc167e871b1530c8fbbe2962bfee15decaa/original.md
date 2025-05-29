```julia
generate_ci_problem(
    pb,
    bifprob,
    sol,
    tspan;
    optimal_period,
    ktrap...
)

```

Generate a periodic orbit problem from a solution.

## Arguments

  * `pb` a `PeriodicOrbitTrapProblem` which provides basic information, like the number of time slices `M`
  * `bifprob` a bifurcation problem to provide the vector field
  * `sol` basically, and `ODEProblem`
  * `tspan = (0,1.)` estimate of the time span (period) of the periodic orbit

## Output

  * returns a `PeriodicOrbitTrapProblem` and an initial guess.
