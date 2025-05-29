```
sklf_right!(A, E, B, F, C, G, D, H; fast = true, atol1 = 0, atol2 = 0, atol3 = 0, rtol, withQ = true, withZ = true) -> (Q, Z, nc)
```

Reduce the partitioned full row rank matrix pencil 

```
  M - λN = | B-λF | A-λE | n
              m      n
```

with `A-λE` regular, to an equivalent form `Mt - λNt = Q'*(M - λN)*Z = | Bt-λFt | At-λEt |`  using orthogonal or unitary transformation matrices `Q` and `Z`,  such that `M - λN` is transformed into a Kronecker-like form `| Bt-λFt | At-λEt |` exhibiting its  right, finite and infinite Kronecker structures (also known as the strong controllability form):

```
                         | Bc-λFc | Ac-λEc     *     | nc
  | Bt-λFt | At-λEt | =  |--------|------------------|
                         |   0    |   0     Auc-λEuc | n-nc
                             m        nc      n-nc
```

The matrices `Bt`, `Ft`, `At`, `Et`, determined from `[Bt At] = Q'*[B A]*Z`, `[Ft Et] = Q'*[F E]*Z`,  are returned in `B`, `F`, `A` and `E`, respectively.  Furthermore, the matrices `Ct`, `Dt`, `Gt`, `Ht`, determined from the compatibly partitioned matrices `[Dt Ct] = [D C]*Z` and `[Ht Gt] = [D C]*Z`, are returned in `C`, `D`, `G` and `H`, respectively  (unless `C`, `D`, `G` and `H` are set to `missing`).

The subpencil `| Bc-λFc | Ac-λEc |` has full row rank `nc` and the `(n-nc) x (n-nc)`  subpencil `Auc-λEuc` contains the finite and infinite eigenvalues of `M - λN`  (also called the uncontrollable eigenvalues of `M - λN`).  

The `(m+n) x (m+n)` orthogonal matrix `Z` has the partitioned form

```
       | Z11 |  0  |  *  | m 
   Z = |-----|-----|-----|
       |  *  |  *  |  *  | n
          m    nc    n-nc
```

with the leading `m x m` submatrix `Z11` invertible and upper triangular. 

`Note:` If `Ct-λGt` is partitioned as  `[ Cc-λGc | Cuc-λGuc ]`, then the following relation is fulfilled

```
  (Cc-λGc)*inv(λEc-Ac)(Bc-λFc) + Dt-λHt = ((C-λG)*inv(λE-A)(B-λF) + D-λH)*Z11
```

and the structured pencil linearization (Ac-λEc,Bc-λFc,Cc-λGc,Dt-λHt) is `strongly controllable`. 

The keyword arguments `atol1`, `atol2`, , `atol3`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A` and `B`, the absolute tolerance for the nonzero elements of `E` and `F`,  and the relative tolerance for the nonzero elements of `A`, `B`, `E` and `F`.   The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed orthogonal or unitary left transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed orthogonal or unitary right transformations are accumulated in the matrix `Z` if `withZ = true`.  If `withZ = false`, `Z` contains the upper triangular matrix `Z11`.   
