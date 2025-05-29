```
solve(prob::ForcedModalTimeProblem)
```

Compute the forced response of a multi-degrees of freedom (Mdof) system due to an arbitrary excitation using the modal approach.

**Inputs**

  * `prob`: Structure containing the parameters of the Mdof problem
  * `method`: Method to compute the Duhamel's integral

      * `:filt`: Filtering using the Z-transform of the impulse response (default)
      * `:interp`: Interpolation + Gaussian quadrature
      * `:conv`: Convolution

**Output**

  * `sol`: ModalTimeSolution structure containing the response of the system at the given time points
