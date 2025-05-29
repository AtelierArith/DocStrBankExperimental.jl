```
ssblkdiag(A, B, C; smarg, disc = false, stable_unstable = false, withQ = true, withZ = true) -> (At, Bt, Ct, Q, Z, blkdims, sep)
```

Reduce the regular matrix pencil `A - λI` to an equivalent block diagonal triangular form `At - λI = Q*(A - λI)*Z`  using the transformation matrices `Q` and `Z`, where `Q = inv(Z)`, such that the transformed matrix `At` have  separated stable and unstable eigenvalues with respect to a stability domain `Cs` defined by the  stability margin parameter `smarg` and the stability type parameter `disc`.  If `disc = false`, `Cs` is the set of complex numbers with real parts less than `smarg`,  while if `disc = true`, `Cs` is the set of complex numbers with moduli less than `smarg` (i.e., the interior of a disc  of radius `smarg` centered in the origin). If `smarg = missing`, the default value used is `smarg = 0`, if  `disc = false`, and `smarg = 1`, if `disc = true`. The matrix `At` results in the following block diagonal form

```
    At = | A1  0  |
         | 0   A2 |
```

where the `n1 x n1` matrix `A1` and the `n2 x n2` matrix `A2` are in Schur form.  The matrix `A1` has unstable eigenvalues and `A2` has stable eigenvalues if `stable_unstable = false`, while `A1` has stable eigenvalues and `A2` has unstable eigenvalues if `stable_unstable = true`. The dimensions of the diagonal blocks are returned in `blkdims = (n1, n2)`.    If `withQ = true`, `Q` contains the left transformation matrix. If `withQ = false`, `Q` is set to `nothing`.    If `withZ = true`, `Z` contains the right transformation matrix. If `withZ = false`, `Z` is set to `nothing`.    `Bt = Q*B`, unless `B = missing`, in which case `Bt = missing` is returned, and `Ct = C*Z`,  unless `C = missing`, in which case `Ct = missing` is returned .               An estimation of the separation of the spectra of the two underlying diagonal blocks is returned in `sep`,  where  `0 ≤ sep ≤ 1`. A value `sep ≈ 0` indicates that `A1` and `A2` have some almost equal eigenvalues. 
