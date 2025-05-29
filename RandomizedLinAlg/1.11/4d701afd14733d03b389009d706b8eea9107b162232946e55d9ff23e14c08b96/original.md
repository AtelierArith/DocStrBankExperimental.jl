```
reigen(A, l)
```

Compute the spectral (`Eigen`) decomposition of `A` using a randomized algorithm.

# Arguments

  * `A`: input matrix.
  * `l::Int`: number of eigenpairs to find.

# Output

  * `::LinearAlgebra.Eigen`: eigen decomposition.

# Implementation note

This is a wrapper around `eigen_onepass()` which uses the randomized samples found using `srft(l)`.
