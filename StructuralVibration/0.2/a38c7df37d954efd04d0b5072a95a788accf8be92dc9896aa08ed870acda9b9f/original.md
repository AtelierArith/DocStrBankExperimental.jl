```
solve(prob::FreeModalTimeProblem)
```

Compute the free response of a multi-degrees of freedom (Mdof) system using the modal approach.

**Inputs**

  * `prob`: Structure containing the parameters of the Mdof problem

**Output**

  * `sol`: ModalTimeSolution structure containing the response of the system at the given time points
