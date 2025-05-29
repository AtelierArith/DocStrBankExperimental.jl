```
solve(prob::DirectFRF; type = :dis, ismat = false, progress = true)
solve(prob::ModalFRFProblem; type = :dis, ismat = false, progress = true)
```

Computes the FRF matrix by direct or modal approach

**Inputs**

  * `prob`: Structure containing the problem data
  * `type`: Type of FRF to compute

      * `:dis`: Admittance (default)
      * `:vel`: Mobility
      * `:acc`: Accelerance
  * `ismat`: Return the FRF matrix as a 3D array (default = false)
  * `progress`: Show progress bar (default = true)

**Output**

  * `sol`: Solution of the problem

      * `u`: FRF matrix
