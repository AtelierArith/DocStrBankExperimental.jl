```
eigvecs(S::Schur{Complex{<:AbstractFloat}}; left=false) -> Matrix
```

Compute right or left eigenvectors from a Schur decomposition. Eigenvectors are returned as columns of a matrix, ordered to match `S.values`. The returned eigenvectors have unit Euclidean norm, and the largest elements are real.
