```
sreduceBF(A, E, B, C, D; fast = true, atol = 0, rtol, withQ = true, withZ = true) -> F, G, Q, Z, n, m, p
```

Reduce the partitioned matrix pencil `M - λN` 

```
           | A-λE | B | ndx
  M - λN = |------|---|
           |  C   | D | ny
              nx    nu
```

to an equivalent basic form `F - λG = Q'*(M - λN)*Z` using orthogonal transformation matrices `Q` and `Z`  such that `M - λN` is transformed into the following standard form

```
           | B1 | A1-λE1 | n
  F - λG = |----|--------|   ,        
           | D1 |   C1   | p
             m      n
```

where `E1` is an `nxn` non-singular matrix, and `A1`, `B1`, `C1`, `D1` are `nxn`-, `nxm`-, `pxn`- and `pxm`-dimensional matrices, respectively. The order `n` of `E1` is equal to the numerical rank of `E` determined using the absolute tolerance `atol` and  relative tolerance `rtol`. The dimensions `m` and `p` are computed as `m = nu + (nx-n)` and `p = ny + (ndx-n)`. 

If `fast = true`, `E1` is determined upper triangular using a rank revealing QR-decomposition with column pivoting of `E`  and `n` is evaluated as the number of nonzero diagonal elements of the R factor, whose magnitudes are greater than  `tol = max(atol,abs(R[1,1])*rtol)`.  If `fast = false`,  `E1` is determined diagonal using a rank revealing SVD-decomposition of `E` and  `n` is evaluated as the number of singular values greater than `tol = max(atol,smax*rtol)`, where `smax`  is the largest singular value.  The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  
