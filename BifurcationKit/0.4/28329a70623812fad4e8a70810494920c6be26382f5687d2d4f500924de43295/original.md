```julia
generate_ci_problem(
    pb,
    bifprob,
    prob_de,
    sol,
    tspan;
    alg,
    ksh...
)

```

Generate a periodic orbit problem from a solution.

## Arguments

  * `pb` a `PoincareShootingProblem` which provides basic information, like the number of time slices `M`
  * `bifprob` a bifurcation problem to provide the vector field
  * `prob_de::ODEProblem` associated to `sol`
  * `sol` basically, and `ODEProblem
  * `period` estimate of the period of the periodic orbit
  * `k` kwargs arguments passed to the constructor of `ShootingProblem`

## Output

  * returns a `ShootingProblem` and an initial guess.
