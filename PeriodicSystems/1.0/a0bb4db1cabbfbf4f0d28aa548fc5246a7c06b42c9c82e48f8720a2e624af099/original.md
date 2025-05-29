```
isstable(psys; smarg = 1, fast = false, offset = sqrt(ϵ)) -> Bool
```

Return `true` if the discrete-time periodic system `psys` has only stable characteristic multipliers and `false` otherwise. 

To assess the stability, the absolute values of the characteristic multipliers (i.e., the eigenvalues of the monodromy matrix) must be less than `smarg-β`, where `smarg` is the discrete-time stability margin (default: `smarg = 1`)  and  `β` is an offset specified via the keyword parameter `offset = β` to be used to numerically assess the stability of eigenvalues. The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

If `fast = false` (default) then the characteristic multipliers are computed using an approach based on the periodic Schur decomposition [1], while if `fast = true`  the structure exploiting reduction [2] of an appropriate lifted pencil is employed.  This later option may occasionally lead to inaccurate results for large number of matrices. 

*References*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
