```
solve(prob::StateSpaceFreqProblem; type = :dis, progress = true)
solve(prob::StateSpaceFreqProblem; type = :dis, progress = true)
```

Computes the frequency response by direct or modal method

**Inputs**

  * `prob`: Structure containing the problem data
  * `type::Symbol`: Type of FRF to compute

      * `:dis`: Displacement
      * `:vel`: Velocity
      * `:acc`: Acceleration
  * `progress`: Show progress bar

**Output** `sol`: Solution of the problem     * `u`: Response spectrum matrix
