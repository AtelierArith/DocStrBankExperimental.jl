```
salocinf(A, E, B; atol1 = 0, atol2 = 0, atol3 = 0, rtol, fast = true) -> (F, G, Scl, blkdims)
```

Compute for the controllable pair `(A-λE,B)`, with `A-λE` a regular pencil, two matrices `F` and `G` such that all eigenvalues of the  pencil `A+B*F-λ(E+B*G)` are infinite. For a pair `(A-λE,B)` with fixed (uncontrollable) finite eigenvalues, only the assignable (controllable)  finite eigenvalues are moved to infinity. 

For a pair `(A-λE,B)` with `A` of order `n`, the number of assignable infinite eigenvalues is `nia := n-ninf-nfu`,   where `ninf` is the number of infinite eigenvalues of `A-λE` and `nfu` is the number of fixed finite eigenvalues of `A-λE`.  The assignable finite eigenvalues are called the *controllable finite eigenvalues*,  while the fixed finite eigenvalues are called the *uncontrollable finite eigenvalues* (these are the finite zeros of the pencil `[A-λE B]`).  The spectrum allocation is achieved by successively replacing the controllable finite eigenvalues of `A-λE` with infinite eigenvalues.  All infinite eigenvalues of `A-λE` are kept unalterred.

The keyword arguments `atol1`, `atol2`, `atol3`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`, the absolute tolerance for the nonzero elements of `B`,   and the relative tolerance for the nonzero elements of `A`, `E` and `B`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the machine epsilon of the element type of `A`. 

The preliminary separation of finite and infinite eigenvalues is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The resulting pencil `Acl-λEcl := Q'*(A+B*F-λ(E+B*G))*Z`,  where `Q` and `Z` are the   orthogonal/unitary matrices used to obtain the pair `(Acl,Ecl)` in a generalized Schur form (GSF), has the form

```
            ( Aig-λEig    *        *     )     
 Acl-λEcl = (   0      Aia-λEia    *     )  
            (   0         0     Afu-λEfu )
```

where: `Aig-λEig` with `Aig` upper triangular and invertible and `Eig` upper triangular and nilpotent, contains the `ninf` infinite eigenvalues of `A-λE`;  `Aia-λEia`, with `Aia` upper triangular and invertible and `Eia` upper triangular and nilpotent, contains `nia` assigned infinite generalized eigenvalues;  and `Afu-λEfu`, with the pair `(Afu,Efu)` in a generalized Schur form,  contains `nfu` fixed (uncontrollable) finite eigenvalues of `A-λE`.  The matrices `Acl`, `Ecl`, `Q`, `Z` and the vectors `α` and `β` such that `α./β` are the generalized eigenvalues of  the pair `(Acl,Ecl)` are returned in the `GeneralizeSchur` object `Scl`.  The values of `ninf`, `nia` and `nfu` are returned in the 3-dimensional vector `blkdims = [ninf, nia, nfu]`.

Method:  For a general pair `(A-λE,B)` the modified generalized Schur method of [1] is used to determine `F` and `G` such that the pair `(A+B*F,E+B*G)` has only infinite eigenvalues.

References:

[1] A. Varga.      On stabilization methods of descriptor systems.     Systems & Control Letters, vol. 24, pp.133-138, 1995.
