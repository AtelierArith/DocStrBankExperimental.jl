```
DirectFreqProblem(K, M, C, F, freq, So)
```

Structure containing the data feeding the direct solver for calculating the modal frequencies

**Fields**

  * `K::AbstractMatrix`: Stiffness matrix
  * `M::AbstractMatrix`: Mass matrix
  * `C::AbstractMatrix`: Damping matrix
  * `F::AbstractMatrix`: Force matrix
  * `freq::AbstractRange`: Frequencies of interest
  * `So::AbstractMatrix`: Selection matrix for observation points
