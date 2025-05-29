```
sklf_left!(A, E, C, G, B, F, D, H; fast = true, atol1 = 0, atol2 = 0, atol3 = 0, rtol, withQ = true, withZ = true) -> (Q, Z, no)
```

Reduce the partitioned full row rank matrix pencil 

```
M - λN = | A-λE | n
         | C-λG | p
            n
```

with `A-λE` regular, to an equivalent form `F - λG = Q'*(M - λN)*Z`  using orthogonal or unitary transformation matrices `Q` and `Z`  such that `M - λN` is transformed into a staircase form exhibiting the left,  finite and infinite Kronecker structures (also known as the strong observability form):

```
                | Auo-λEuo  |   *    | n-no
  | At-λEt |    |   0       | Ao-λEo | no
  |--------| =  |-----------|--------|
  | Ct-λGt |    |   0       | Co-λGo | p
                   n-no         no
```

The matrices `Ct`, `Gt`, `At`, `Et`, determined from `[At; Ct] = Q'*[A; C]*Z`, `[Et; Gt] = Q'*[E; G]*Z`,   are returned in `C`, `G`, `A` and `E`, respectively.  Furthermore, the matrices `Bt`, `Dt`, `Ft`, `Ht` determined from the compatibly partitioned `[Bt; Dt] = Q'*[B; D]` and `[Ft; Ht] = Q'*[F; H]`, are returned in `B`, `D`, `F`, and `H`, respectively (unless `B`, `D`, `F` and `H` are set to `missing`).

The subpencil 

```
   | Ao-λEo |   
   |--------|
   | Co-λGo |
```

has full column rank `no` and the `(n-no) x (n-no)` subpencil `Auo-λEuo` contains the finite and infinite  eigenvalues of `M - λN` (also called the unobservable eigenvalues of `M - λN`).  

The  `(n+p) x (n+p)` orthogonal matrix `Q` has the partitioned form

```
       |  *  |  *  |  *   | n 
   Q = |-----|-----|------|
       |  *  |  0  | Q22  | p
         n-no  no     p
```

with the `p x p` trailing submatrix `Q22` invertible and upper triangular. 

`Note:` If `Bt-λFt` is partitioned as  `[ Buo-λFuo | Bo-λFo ]`, then the following relation is fulfilled

```
  (Co-λGo)*inv(λEo-Ao)(Bo-λFo) + Dt-λHt = Q22'*((C-λG)*inv(λE-A)(B-λF) + D-λH)
```

and the structured pencil linearization (Ao-λEo,Bo-λFo,Co-λGo,Dt-λHt) is `strongly observable`. 

The keyword arguments `atol1`, `atol2`, , `atol3`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A` and `C`, the absolute tolerance for the nonzero elements of `E` and `G`,  and the relative tolerance for the nonzero elements of `A`, `C`, `E` and `G`.   The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed orthogonal or unitary left transformations are accumulated in the matrix `Q` if `withQ = true`.  If `withQ = false`, `Q` contains the upper triangular matrix `Q22`.    The performed orthogonal or unitary right transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.   
