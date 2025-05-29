```
solve(prob::SdofFreeTimeProblem)
```

Compute the free response of a single degree of freedom (Sdof) system.

**Input**

  * `prob`: Structure containing the parameters of the Sdof problem

**Output**

  * `sol`: The response of the system at the given time points

      * `u`: Displacement solution
      * `du`: Velocity solution
      * `ddu`: Acceleration solution
