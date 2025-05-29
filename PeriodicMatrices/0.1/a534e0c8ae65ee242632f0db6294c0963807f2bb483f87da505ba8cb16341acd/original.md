```
 ev = peigvals(A::Array{T,3}; rev = true, fast = false)
```

Compute the eigenvalues of a product of `p` square matrices  `A(p)...*A(2)*A(1)`, if `rev = true` (default) (also called characteristic multipliers) or  of `A(1)*A(2)...A(p)` if `rev = false`, without evaluating the product.  The matrices `A(1)`, `...`, `A(p)` are contained in the `n×n×p` array `A`  such that the `i`-th matrix `A(i)` is contained in `A[:,:,i]`. If `fast = false` (default) then the eigenvalues are computed using an approach based on the periodic Schur decomposition [1], while if `fast = true`  the structure exploiting reduction [2] of an appropriate lifted pencil is employed. This later option may occasionally lead to inaccurate results for large number of matrices. 

*References*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
