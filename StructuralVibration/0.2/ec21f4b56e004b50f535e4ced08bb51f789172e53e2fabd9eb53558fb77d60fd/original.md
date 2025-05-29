```
solve(prob::SdofHarmonicTimeProblem)
```

Computes the forced response of a single degree of freedom (Sdof) system due to an harmonic external force or base motion

**Inputs**

  * `prob`: Structure containing the parameters of the Sdof harmonic problem

**Output**

  * `sol`: The response of the system at the given time points

      * `u`: Displacement solution
      * `du`: Velocity solution
      * `ddu`: Acceleration solution
