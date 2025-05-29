```
ProjectedBasis(;L, N, base=2, alloc=1000, threaded=true)
```

Construction method for `ProjectedBasis` with fixed particle number (or total U(1) charge).

## Inputs:

  * `dtype`   : Data type for indices.
  * `L`       : Length of the system.
  * `N`       : Quantum number of up spins / particle number / U(1) charge.
  * `base`    : Base, default = 2.
  * `alloc`   : Size of the prealloc memory for the basis content, used only in multithreading, default = 1000.
  * `threaded`: Whether use the multithreading, default = true.
  * `small_N` : Whether use the small-N algorithm.

## Outputs:

  * `b` : ProjectedBasis.
