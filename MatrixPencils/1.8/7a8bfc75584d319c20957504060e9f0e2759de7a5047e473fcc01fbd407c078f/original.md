```
_svdlikeAE!(A, E, Q, Z, B, C; svdA = true, fast = true, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (rE, rA22)
```

Reduce the regular matrix pencil `A - λE` to an equivalent form `A1 - λE1 = Q1'*(A - λE)*Z1` using  orthogonal or unitary transformation matrices `Q1` and `Z1` such that the transformed matrices `A1` and `E1`  are, for `svdA = true`, in the following SVD-like coordinate form

```
               | A11-λE11 |  A12  |  A13  |
               |----------|-------|-------|
    A1 - λE1 = |    A21   |  A22  |   0   | ,
               |----------|-------|-------|
               |    A31   |   0   |   0   |
```

where the `rE x rE` matrix `E11` and `rA22 x rA22` matrix `A22` are nosingular, and `E11` and `A22` are upper triangular,  if `fast = true`, and diagonal, if `fast = false`. 

If `svdA = false`, only `E` is reduced to SVD-like form and `A1 - λE1` has the form

```
               | A11-λE11 |  A12  |
    A1 - λE1 = |----------|-------| , 
               |    A21   |  A22  |
```

where the `rE x rE` matrix `E11` is nonsingular upper triangular, if `fast = true`,  and diagonal, if `fast = false`, and `A22` is unreduced and has rank `rA22`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance  for the nonzero elements of `A` and `E`. 

The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations Q1 are accumulated in the matrix `Q <- Q*Q1`  if `withQ = true`. Otherwise, `Q` is unchanged.    The performed right orthogonal or unitary transformations Z1 are accumulated in the matrix `Z <- Z*Z1` if `withZ = true`.  Otherwise, `Z` is unchanged.  

`Q1'*B` is returned in `B` unless `B = missing` and `C*Z1` is returned in `C` unless `C = missing` .              
