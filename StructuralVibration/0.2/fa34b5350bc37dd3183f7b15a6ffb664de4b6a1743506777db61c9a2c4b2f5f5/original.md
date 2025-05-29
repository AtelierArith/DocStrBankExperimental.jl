```
solve(prob::HarmonicModalTimeProblem)
```

Compute the forced response of a multi-degrees of freedom (Mdof) system due to an harmonic excitation using the modal approach.

**Inputs**

  * `prob`: Structure containing the parameters of the Mdof problem

**Output**

  * `sol`: Solution structure containing the response of the system at the given time points

      * `u`: Displacement
      * `du`: Velocity
      * `ddu`: Acceleration
