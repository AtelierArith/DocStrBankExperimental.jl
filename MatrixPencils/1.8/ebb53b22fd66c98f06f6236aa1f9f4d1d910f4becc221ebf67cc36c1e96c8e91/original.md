```
sklf_rightfin!(A, E, B, C; fast = true, atol1 = 0, atol2 = 0,  
               rtol, withQ = true, withZ = true) -> (Q, Z, νr, nc, nuc)
```

Reduce the partitioned full row rank matrix pencil 

```
  M - λN = | B | A-λE | n
             m    n
```

with `A-λE` regular, to an equivalent form `F - λG = Q'*(M - λN)*diag(I,Z)`  using orthogonal or unitary transformation matrices `Q` and `Z`  such that `M - λN` is transformed into a staircase form `| Bt | At-λEt |` exhibiting the separation of its finite eigenvalues:

```
                     |  Bc | Ac-λEc     *    | nc
  | Bt | At-λEt | =  |-----|-----------------|
                     |  0  |  0     Auc-λEuc | nuc
                        m     nc      nuc
```

`Bt = Q'*B`, `At = Q'*A*Z`and `Et = Q'*E*Z` are returned in `B`, `A` and `E`, respectively, and `C*Z` is returned in `C` (unless `C = missing`).  The resulting `Et` is upper triangular. If `E` is already upper triangular, then  the preliminary reduction of `E` to upper triangular form is not performed.                

The subpencil `| Bc | Ac-λEc |` has full row rank `nc` for all finite values of `λ`, is in a staircase form, and,  if E is invertible, contains the right Kronecker indices of `M - λN`.  The `nr`-dimensional vector `νr` contains the row and column dimensions of the blocks of the staircase form  `| Bc | Ac-λI |` such that `i`-th block has dimensions `νr[i] x νr[i-1]` (with `νr[0] = m`) and  has full row rank. If E is invertible, the difference `νr[i-1]-νr[i]` for `i = 1, 2, ..., nr` is the number of elementary Kronecker blocks of size `(i-1) x i`.

The `nuc x nuc` subpencil `Auc-λEuc` contains the finite eigenvalues of `M - λN` (also called the uncontrollable finite eigenvalues of `A - λE`).  If E is singular, `Auc-λEuc` may also contain a part of the infinite eigenvalues of `M - λN` (also called the uncontrollable infinite eigenvalues of `A - λE`).

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `B`,   and the relative tolerance for the nonzero elements of `A` and `B`.   The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed orthogonal or unitary left transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed orthogonal or unitary right transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.   

`Note:` This function, called with reversed input parameters `E` and `A` (i.e., instead `A` and `E`), performs the  separation all infinite and nonzero finite eigenvalues of the pencil `M - λN`.
