```
solve(prob::StateSpaceFRFProblem; type = :dis, ismat = false, progress = true)
solve(prob::StateSpaceModalFRFProblem; type = :dis, ismat = false, progress = true)
```

Computes the FRF matrix by direct or modal method

**Inputs**

  * `prob`: Structure containing the problem data
  * `type`: Type of FRF to compute

      * `:dis`: Admittance
      * `:vel`: Mobility
      * `:acc`: Accelerance
  * `ismat`: Return the FRF matrix as a 3D array (default = false)
  * `progress`: Show progress bar (default = true)

**Output**

  * `sol`: FRFSolution structure

      * `u`: FRF matrix
