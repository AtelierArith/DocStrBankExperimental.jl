```
preduceBF(M, N; fast = true, atol = 0, rtol, withQ = true, withZ = true) -> (F, G, Q, Z, n, m, p)
```

Reduce the matrix pencil `M - λN` to an equivalent form `F - λG = Q'*(M - λN)*Z` using  orthogonal or unitary transformation matrices `Q` and `Z` such that the pencil `M - λN` is transformed  into the following standard form

```
               | B  | A-λE | 
      F - λG = |----|------| ,        
               | D  |  C   |
```

where `E` is an `nxn` non-singular matrix, and `A`, `B`, `C`, `D` are `nxn`-, `nxm`-, `pxn`- and `pxm`-dimensional matrices, respectively. The order `n` of `E` is equal to the numerical rank of `N` determined using the absolute tolerance `atol` and  relative tolerance `rtol`. `M` and `N` are overwritten by `F` and `G`, respectively. 

If `fast = true`, `E` is determined upper triangular using a rank revealing QR-decomposition with column pivoting of `N`  and `n` is evaluated as the number of nonzero diagonal elements of the `R` factor, whose magnitudes are greater than  `tol = max(atol,abs(R[1,1])*rtol)`.  If `fast = false`,  `E` is determined diagonal using a rank revealing SVD-decomposition of `N` and  `n` is evaluated as the number of singular values greater than `tol = max(atol,smax*rtol)`, where `smax`  is the largest singular value.  The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  
