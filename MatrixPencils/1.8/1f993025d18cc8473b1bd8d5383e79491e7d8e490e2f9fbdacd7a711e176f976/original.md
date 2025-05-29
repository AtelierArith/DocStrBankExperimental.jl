```
sklf_rightfin2!(A, E, B, m1, C; fast = true, atol1 = 0, atol2 = 0,  
               rtol, withQ = true, withZ = true) -> (Q, Z, νr, nc, nuc)
```

Reduce the partitioned full row rank matrix pencil 

```
  M - λN = [ B | A-λE ] n  = [ B1  B2 | A-λE ] n
             m    n            m1 m-m1   n
```

with `A-λE` regular, to an equivalent form `F - λG = Q'*(M - λN)*diag(I,Z)`  using orthogonal or unitary transformation matrices `Q` and `Z`  such that `M - λN` is transformed into a staircase form `[ Bt | At-λEt ]` exhibiting  the separation of its finite eigenvalues:

```
                     [  Bc | Ac-λEc     *    ] nc
  [ Bt | At-λEt ] =  [-----|-----------------]
                     [  0  |  0     Auc-λEuc ] nuc
                        m     nc      nuc
```

`Bt = Q'*B`, `At = Q'*A*Z`and `Et = Q'*E*Z` are returned in `B`, `A` and `E`, respectively, and `C*Z` is returned in `C` (unless `C = missing`).  The resulting `Et` is upper triangular. If `E` is already upper triangular, then  the preliminary reduction of `E` to upper triangular form is not performed.                

The subpencil `[ Bc | Ac-λEc ]` has full row rank `nc` for all finite values of `λ`, with `[ Bc | Ac ] = [ Bc1 Bc2 | Ac]` in a staircase form

```
                    m1  m-m1  νr[1] νr[2] . . .  νr[p-2] 
                  [ B11 B12 | A11   A12   . . .  A1,p-2  A1,p-1  A1p ]  νr[1]
                  [  0  B22 | A21   A22   . . .  A2,p-2  A2,p-1  A2p ]  νr[2]
                  [  0   0  | A31   A32   . . .  A3,p-2  A3,p-1  A3p ]  νr[3]
                  [  0   0  |  0    A42   . . .  A4,p-2  A4,p-1  A4p ]  νr[4]
[ Bc1 Bc2 | Ac] = [  0   0  |  .     .    . . .    .       .      .  ]   .
                  [  0   0  |  .     .      . .    .       .      .  ]   .
                  [  0   0  |  .     .        .    .       .      .  ]   .
                  [  0   0  |  0     0    . . .  Ap,p-2  Ap,p-1  App ]  νr[p]
```

where the blocks  `B11`, `B22`, `A31`, ..., `Ap,p-2`  have full row ranks. The `p`-dimensional vector `νr`, with `p = 2nr` even,  contains the row dimensions of the  blocks.  The difference `νr[2i-1]+νr[2i]-νr[2i+1]-νr[2i+2]` for `i = 1, 2, ..., nr` is the  number of elementary Kronecker blocks of size `(i-1) x i`.

The `nuc x nuc` subpencil `Auc-λEuc` contains the finite eigenvalues of `M - λN` (also called the uncontrollable finite eigenvalues of `A - λE`).  If E is singular, `Auc-λEuc` may also contain a part of the infinite eigenvalues of `M - λN` (also called the uncontrollable infinite eigenvalues of `A - λE`).

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `B`,   and the relative tolerance for the nonzero elements of `A` and `B`.   The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed orthogonal or unitary left transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed orthogonal or unitary right transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.   

Method: The implemented algorithm [1] represents a specialization of the  controllability staircase algorithm of [2] to the special structure of the input matrix `B = [B1,B2]`.

References

[1] Varga, A. Reliable algorithms for computing minimal dynamic covers for descriptor systems.     Proc. of MTNS'04, Leuven, Belgium, 2004.

[2] Varga, A. Computation of Irreducible Generalized State-Space Realizations.     Kybernetika, vol. 26, pp. 89-106, 1990.
