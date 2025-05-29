```
solve(prob::StateSpaceTimeProblem, method = :zoh; progress = true)
```

Solves a discrete-time problem using the state-space model

**Inputs**

  * `prob`: Discrete-time problem
  * `method`: Discretization method

      * `:zoh`: Zero-order Hold method
      * `:foh`: First-order Hold method
      * `:blh`: Band-limited Hold method
      * `:rk4`: Runge-Kutta 4th order method
  * `progress`: Show progress bar (default = true)

**Output**

  * `StateSpaceSolution`: Solution of the state-space model
