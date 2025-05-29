cm = pseig(A::PeriodicMatrix[, k = 1]; fast = false) 

Compute the characteristic multipliers of a discrete-time periodic matrix `A(t)`.  `A` is given as a `PeriodicMatrix`. The characteristic multipliers are computed   as the eigenvalues of the reverse product of component matrices,  without evaluating the product.  The argument `k` specifies the starting index of component matrices (default: `k = 1`).  If `fast = false` (default) then the eigenvalues are computed using an approach based on the periodic Schur decomposition [1], while if `fast = true`  the structure exploiting reduction [2] of an appropriate lifted pencil is employed.  This later option may occasionally lead to inaccurate results for large number of matrices. 

*Note:* The first `nmin` components of `cm` contains the `core characteristic multipliers`, where `nmin` is the minimum row dimensions of component matrices,  while the last `ncur-nmin` components of `cm` are zero,  where `ncur` is the column dimension of the `k`-th component matrix. 

*References*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
