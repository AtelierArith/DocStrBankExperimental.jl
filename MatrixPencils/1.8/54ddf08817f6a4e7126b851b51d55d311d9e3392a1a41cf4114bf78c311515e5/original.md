```
sklf_leftfin!(A, E, C, B; fast = true, atol1 = 0, atol2 = 0,  
              rtol, withQ = true, withZ = true) -> (Q, Z, μl, no, nuo)
```

Reduce the partitioned full column rank matrix pencil 

```
  M - λN = | A-λE | n
           |  C   | p
              n
```

with `A-λE` regular, to an equivalent form `F - λG = Q'*(M - λN)*diag(I,Z)`  using orthogonal or unitary transformation matrices `Q` and `Z`  such that `M - λN` is transformed into a staircase form exhibiting the separation of its finite eigenvalues:

```
                | Auo-λEuo  |   *    | nuo
  | At-λEt |    |   0       | Ao-λEo | no
  |--------| =  |-----------|--------|
  |  Ct    |    |   0       |   Co   | p
                    nuo         no
```

`Ct = C*Z`, `At = Q'*A*Z` and `Et = Q'*E*Z` are returned in `C`, `A` and `E`, respectively,  and `Q'*B` is returned in `B` (unless `B = missing`).    The resulting `Et` is upper triangular. If `E` is already upper triangular, then  the preliminary reduction of `E` to upper triangular form is not performed.                

The subpencil `| Ao-λEo |` has full column rank `no` for all finite values of `λ`, is in a staircase form,                `|   Co   |` and, if `E` is nonsingular, contains the left Kronecker indices of `M - λN`. The `nl`-dimensional vector `μl` contains the row and column dimensions of the blocks of the staircase form such that `i`-th block has dimensions `μl[nl-i] x μl[nl-i+1]` (with μl[0] = p) and  has full column rank. If `E` is nonsingular, the difference `μl[nl-i]-μl[nl-i+1]` for `i = 1, 2, ..., nl` is the number of elementary Kronecker blocks of size `i x (i-1)`.

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `C`,   and the relative tolerance for the nonzero elements of `A` and `C`.   The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed orthogonal or unitary left transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed orthogonal or unitary right transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.   

`Note:` This function, called with reversed input parameters `E` and `A` (i.e., instead `A` and `E`), performs the  separation all infinite and nonzero finite eigenvalues of the pencil `M - λN`.
