```
DirectFRFProblem(K, M, C, freq, So, Se)
```

Structure containing the data feeding the direct solver for calculating an FRF

**Fields**

  * `K::AbstractMatrix`: Stiffness matrix
  * `M::AbstractMatrix`: Mass matrix
  * `C::AbstractMatrix`: Damping matrix
  * `freq::AbtractRange`: Frequencies of interest
  * `So::AbstractMatrix`: Selection matrix for observation points
  * `Se::AbstractMatrix`: Selection matrix for excitation points
