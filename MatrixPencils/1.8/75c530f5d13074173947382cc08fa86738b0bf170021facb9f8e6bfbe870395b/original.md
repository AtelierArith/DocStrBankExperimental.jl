```
sklf_left!(A, C, B; fast = true, atol1 = 0, atol2 = 0, rtol, withQ = true) -> (Q, μl, no, nuo)
```

Reduce the partitioned full column rank matrix pencil 

```
  M - λN = | A-λI | n
           |  C   | p
              n
```

to an equivalent form `F - λL = diag(Q',I)*(M - λN)*Q` using orthogonal or unitary transformation matrix `Q`   such that `M - λN` is transformed into a Kronecker-like form  exhibiting its  finite  and left Kronecker structures (also known as the observability staircase form):

```
               | Auo-λI  |  *    | nuo
  | At-λI |    |    0    | Ao-λI | no
  |-------| =  |---------|-------|
  |  Ct   |    |    0    |   Co  | p
                   nuo       no
```

`Ct = C*Q` and `At = Q'*A*Q` are returned in `C` and `A`, respectively, and `Q'*B` is returned in `B` (unless `B = missing`).                 

The subpencil `| Ao-λI; Co |` has full column rank `no`, is in a staircase form,  and contains the left Kronecker indices of `M - λN`. 

The `nl`-dimensional vector `μl` contains the row and column dimensions of the blocks of the staircase form such that `i`-th block has dimensions `μl[nl-i] x μl[nl-i+1]` (with μl[0] = p) and  has full column rank. The difference `μl[nl-i]-μl[nl-i+1]` for `i = 1, 2, ..., nl` is the number of elementary Kronecker blocks of size `i x (i-1)`.

The `nuo x nuo` matrix `Auo` contains the (finite) eigenvalues of `M - λN` (also called the unobservable eigenvalues of `A`).  

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `C`,  and the relative tolerance  for the nonzero elements of `A` and `C`.   The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.   
