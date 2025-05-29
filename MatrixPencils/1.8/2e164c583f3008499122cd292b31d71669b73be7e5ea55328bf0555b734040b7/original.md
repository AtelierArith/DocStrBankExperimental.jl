```
sklf_right!(A, B, C; fast = true, atol1 = 0, atol2 = 0, rtol, withQ = true) -> (Q, νr, nc, nuc)
```

Reduce the partitioned full row rank matrix pencil 

```
  M - λN = | B | A-λI | n
             m    n
```

to an equivalent form `F - λG = Q'*(M - λN)*diag(I,Q)` using orthogonal or unitary transformation matrix `Q`   such that `M - λN` is transformed into a Kronecker-like form `| Bt | At-λI |` exhibiting its  right and finite Kronecker structures (also known as the controllability staircase form):

```
                    |  Bc | Ac-λI     *    | nc
  | Bt | At-λI | =  |-----|----------------|
                    |  0  |  0     Auc-λI  | nuc
                       m     nc      nuc
```

`Bt = Q'*B` and `At = Q'*A*Q` are returned in `B` and `A`, respectively, and `C*Q` is returned in `C` (unless `C = missing`).                 

The subpencil `| Bc | Ac-λI |` has full row rank `nc`, is in a staircase form, and contains the right Kronecker indices of `M - λN`.  The `nr`-dimensional vector `νr` contains the row and column dimensions of the blocks of the staircase form  `| Bc | Ac-λI |` such that `i`-th block has dimensions `νr[i] x νr[i-1]` (with `νr[0] = m`) and  has full row rank. The difference `νr[i-1]-νr[i]` for `i = 1, 2, ..., nr` is the number of elementary Kronecker blocks of size `(i-1) x i`.

The `nuc x nuc` matrix `Auc` contains the (finite) eigenvalues of `M - λN` (also called the uncontrollable eigenvalues of `A`).  

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `B`,  and the relative tolerance  for the nonzero elements of `A` and `B`.   The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.   
