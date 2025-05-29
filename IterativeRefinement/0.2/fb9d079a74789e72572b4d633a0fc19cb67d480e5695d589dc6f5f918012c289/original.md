```
rfeigen(A, S::Schur, idxλ, DT, maxiter=5) -> vals, vecs, status
```

Improves the precision of a cluster of eigenvalues of matrix `A` via multi-precision iterative refinement, using more-precise real type `DT`. Returns improved estimates of eigenvalues and vectors generating the corresponding invariant subspace.

This method works on the set of eigenvalues in `S.values` indexed by `idxλ`. It is designed to handle (nearly) defective cases, but will fail if the matrix is extremely non-normal or the initial estimates are poor. Note that `S` must be a true Schur decomposition, not a "real Schur".
