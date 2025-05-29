```
solve(prob::StateTimeSpaceProblem, alg = RK4(); progress = true)
```

Solves a continuous-time problem using the state-space model

**Inputs**

  * `prob`: Continuous-time problem
  * `alg`: Time integration algorithm
  * `progress`: Show progress bar (default = true)

**Output**

  * `StateSpaceSolution`: Solution of the state-space model
