```
 ev = peigvals(A::Vector{Matrix}[, k = 1]; rev = true, fast = false)
```

Compute the eigenvalues of a square cyclic product of `p` matrices  `A(k-1)...*A(2)*A(1)*A(p)...*A(k)`, if `rev = true` (default) or  `A(k)*A(k+1)*...A(p)*A(1)...A(k-1)` if `rev = false`, without evaluating the product.  The argument `k` specifies the starting index (default: `k = 1`).  The matrices `A(1)`, `...`, `A(p)` are contained in the `p`-vector of matrices `A`  such that the `i`-th matrix  `A(i)`, of dimensions `m(i)×n(i)`, is contained in `A[i]`. If `fast = false` (default) then the eigenvalues are computed using an approach based on the periodic Schur decomposition [1], while if `fast = true`  the structure exploiting reduction [2] of an appropriate lifted pencil is employed.  This later option may occasionally lead to inaccurate results for large number of matrices. 

*Note:* The first `nmin` components of `ev` contains the `core eigenvalues` of the appropriate matrix product, where `nmin` is the minimum row dimensions of matrices `A[i]`, for `i = 1, ..., p`,  while the last `ncur-nmin` components of `ev` are zero,  where `ncur` is the column dimension of `A[k]` if `rev = true` or  the row dimension of `A[k]` if `rev = false`. 

*References*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
