```
solve(prob::DirectFreqProblem; type = :dis, progress = true)
solve(prob::ModalFreqProblem; type = :dis, progress = true)
```

Computes the frequency response by direct or modal approach

**Inputs**

  * `prob`: Structure containing the problem data
  * `type`: Type of response to compute

      * `:dis`: Displacement (default)
      * `:vel`: Velocity
      * `:acc`: Acceleration
  * `progress`: Show progress bar (default = true)

**Output**

  * `sol`: Solution of the problem

      * `u`: Response spectrum matrix
