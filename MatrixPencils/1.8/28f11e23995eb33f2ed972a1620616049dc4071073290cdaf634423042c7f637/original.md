```
sklf_right2!(A, B, m1, C; fast = true, atol1 = 0, atol2 = 0, rtol, withQ = true) -> (Q, νr, nc, nuc)
```

Reduce the partitioned full row rank matrix pencil 

```
  M - λN = [ B | A-λI ] n  = [ B1  B2 | A-λI ] n
             m    n            m1 m-m1   n
```

to an equivalent form `F - λG = Q'*(M - λN)*diag(I,Q)` using orthogonal or unitary transformation matrix `Q`   such that `M - λN` is transformed into a Kronecker-like form `[ Bt | At-λI ]` exhibiting its  right and finite Kronecker structures (also known as the controllability staircase form):

```
                    [  Bc | Ac-λI     *    ] nc
  [ Bt | At-λI ] =  [-----|----------------]
                    [  0  |  0     Auc-λI  ] nuc
                       m     nc      nuc
```

`Bt = Q'*B` and `At = Q'*A*Q` are returned in `B` and `A`, respectively, and `C*Q` is returned in `C` (unless `C = missing`).                 

The subpencil `[ Bc | Ac-λI ]` has full row rank `nc` with `[ Bc | Ac ] = [ Bc1 Bc2 | Ac]`  in a staircase form

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

The `nuc x nuc` matrix `Auc` contains the (finite) eigenvalues of `M - λN` (also called the uncontrollable eigenvalues of `A`).  

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `B`,  and the relative tolerance  for the nonzero elements of `A` and `B`.   The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.  

Method: The implemented algorithm [1] represents a specialization of the controllability staircase algorithm of [2]  to the special structure of the input matrix `B = [B1,B2]`.

References:

[1] Varga, A. Reliable algorithms for computing minimal dynamic covers. Proc. CDC'2003, Hawaii, 2003.

[2] Varga, A. Numerically stable algorithm for standard controllability form determination.     Electronics Letters, vol. 17, pp. 74-75, 1981.
