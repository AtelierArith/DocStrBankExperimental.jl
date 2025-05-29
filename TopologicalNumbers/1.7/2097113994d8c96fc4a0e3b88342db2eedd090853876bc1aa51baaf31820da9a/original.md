```
pfaffian_schur(A::AbstractMatrix{T}; overwrite_a=false) where {T<:Real}
```

Calculate Pfaffian of a real antisymmetric matrix using the Schur decomposition. (Hessenberg would in principle be faster, but scipy-0.8 messed up the performance for scipy.linalg.hessenberg()).

This function does not make use of the skew-symmetry of the matrix A, but uses a LAPACK routine that is coded in FORTRAN and hence faster than python. As a consequence, pfaffian_schur is only slightly slower than pfaffian().
