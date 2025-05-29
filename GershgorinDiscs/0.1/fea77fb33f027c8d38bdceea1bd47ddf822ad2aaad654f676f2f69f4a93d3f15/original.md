```
eigvals_extrema(A::AbstractMatrix)
```

Estimate the minimum and maximum eigenvalues of a square matrix `A` using Gershgorin circle theorem.

This function computes the Gershgorin discs for `A` and returns the smallest and largest values that any eigenvalue could have based on the discs.
