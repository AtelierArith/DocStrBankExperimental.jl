```
sklf_left!(A, E, C, B; fast = true, atol1 = 0, atol2 = 0, atol3 = 0, rtol, withQ = true, withZ = true) -> (Q, Z, μl, no, nfuo, niuo)
```

Reduce the partitioned full column rank matrix pencil 

```
  M - λN = | A-λE | n
           |  C   | p
              n
```

to an equivalent form `F - λG = diag(Q',I)*(M - λN)*Z` using orthogonal or unitary transformation matrices `Q`  and `Z`  such that `M - λN` is transformed into a Kronecker-like form  exhibiting its  infinite, finite  and left Kronecker structures (also known as the generalized observability staircase form):

```
                | Aiuo-λEiuo     *       |   *    | niuo
                |    0       Afuo-λEfuo  |   *    | nfuo
  | At-λEt |    |    0           0       | Ao-λEo | no
  |--------| =  |------------------------|--------|
  |  Ct    |    |    0           0       |   Co   | p
                    niuo        nfuo         no
```

`Ct = C*Z`, `At = Q'*A*Z` and `Et = Q'*E*Z` are returned in `C`, `A` and `E`, respectively,  and `Q'*B` is returned in `B` (unless `B = missing`).                 

The subpencil `| Ao-λEo |` has full column rank `no`, is in a staircase form, and contains the left Kronecker indices of `M - λN`.                `|   Co   |` The `nl`-dimensional vector `μl` contains the row and column dimensions of the blocks of the staircase form such that `i`-th block has dimensions `μl[nl-i] x μl[nl-i+1]` (with μl[0] = p) and  has full column rank. The difference `μl[nl-i]-μl[nl-i+1]` for `i = 1, 2, ..., nl` is the number of elementary Kronecker blocks of size `i x (i-1)`.

The `niuo x niuo` subpencil `Aiuo-λEiuo` contains the infinite eigenvalues of `M - λN` (also called the unobservable infinite eigenvalues of `A-λE`).  

The `nfuo x nfuo` subpencil `Afuo-λEfuo` contains the finite eigenvalues of `M - λN` (also called the unobservable finite eigenvalues of `A-λE`).  

The keyword arguments `atol1`, `atol2`, `atol3` and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  the absolute tolerance for the nonzero elements of `C`,  and  the relative tolerance for the nonzero elements of `A`, `E` and `C`.   The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed orthogonal or unitary left transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed orthogonal or unitary right transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.   
