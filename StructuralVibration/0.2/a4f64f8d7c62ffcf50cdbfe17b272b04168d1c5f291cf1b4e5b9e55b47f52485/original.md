```
solve(prob::SdofForcedTimeProblem)
```

Computes the forced response of a single degree of freedom (Sdof) system due to an arbitrary external force or base motion

**Inputs**

  * `prob`: Structure containing the parameters of the Sdof forced problem
  * `method`: Method to compute the Duhamel's integral

      * `:filt`: Filtering using the Z-transform of the impulse response (default)
      * `:interp`: Interpolation + Gaussian quadrature
      * `:conv`: Convolution product

**Output**

  * `sol`: The response of the system at the given time points

      * `u`: Displacement solution
      * `du`: Velocity solution
      * `ddu`: Acceleration solution
