```
NCMSolution(x, resid, alg, iters, solver, stats)
```

Representation of the solution to an NCM problem defined by a `NCMProblem`

## Fields

  * `X`: The solution to the NCM problem.
  * `resid`: The residual of the solver.
  * `alg`: The algorithm used by the solver.
  * `iters`: The number of iterations used to solve the NCM problem.
  * `solver`: The `NCMSolver` object containing the solver's internal cached variables.
  * `stats`: Statistics of the solver.
