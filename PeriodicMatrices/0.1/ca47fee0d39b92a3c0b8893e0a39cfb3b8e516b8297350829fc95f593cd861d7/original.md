```
 cm = pseig(A::PeriodicArray; fast = false)
```

Compute the characteristic multipliers of a discrete-time periodic matrix `A(t)`.  `A` is given as a `PeriodicArray`. The characteristic multipliers are computed   as the eigenvalues of the reverse product of component matrices,  without evaluating the product.  If `fast = false` (default) then the eigenvalues are computed using an approach based on the periodic Schur decomposition [1], while if `fast = true`  the structure exploiting reduction [2] of an appropriate lifted pencil is employed. This later option may occasionally lead to inaccurate results for large number of matrices. 

*References*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
