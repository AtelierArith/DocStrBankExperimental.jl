```julia
generate_ci_problem(
    shooting,
    prob_bif,
    prob_de,
    sol,
    tspan;
    prob_mono,
    alg,
    alg_mono,
    use_bordered_array,
    ksh...
)

```

Generate a periodic orbit problem from a solution.

## Arguments

  * `pb` a `ShootingProblem` which provides basic information, like the number of time slices `M`
  * `bifprob` a bifurcation problem to provide the vector field
  * `prob_de::ODEProblem` associated to `sol`
  * `sol` basically an `ODEProblem` or a function `t -> sol(t)`
  * `tspan::Tuple` estimate of the period of the periodic orbit
  * `alg` algorithm for solving the Cauchy problem
  * `prob_mono` problem for monodromy
  * `alg_mono` algorithm for solving the monodromy Cauchy problem
  * `k` kwargs arguments passed to the constructor of `ShootingProblem`

## Output

  * returns a `ShootingProblem` and an initial guess.
