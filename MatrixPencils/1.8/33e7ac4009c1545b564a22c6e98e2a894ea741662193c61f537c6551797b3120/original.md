```
salocinfd(A, E, C; atol1 = 0, atol2 = 0, atol3 = 0, rtol, sepinf = true, fast = true) -> (K, L, Scl, blkdims)
```

Compute for the pair `(A-λE,C)`, with `A-λE` a regular pencil, the matrices `K` and `L` such that all eigenvalues of the  pencil `A+K*C-λ(E+L*C)` are infinite. For a pair `(A-λE,C)` with fixed (unobservable) finite eigenvalues, only the assignable (observable) finite eigenvalues are moved to infinity. 

For a pair `(A-λE,C)` with `A` of order `n`, the number of assignable infinite eigenvalues is `nia := n-ninf-nfu`,   where `ninf` is the number of infinite eigenvalues of `A-λE` and `nfu` is the number of fixed finite eigenvalues of `A-λE`.  The assignable finite eigenvalues are called the *observable finite eigenvalues*,  while the fixed finite eigenvalues are called the *unobservable finite eigenvalues* (these are the finite zeros of the pencil `[A-λE; C]`).  The spectrum allocation is achieved by successively replacing the observable finite eigenvalues of `A-λE` with infinite eigenvalues.  All infinite eigenvalues of `A-λE` are kept unalterred.

The keyword arguments `atol1`, `atol2`, , `atol3`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`, the absolute tolerance for the nonzero elements of `C`,   and the relative tolerance for the nonzero elements of `A`, `E` and `C`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the machine epsilon of the element type of `A`. 

The preliminary separation of finite and infinite eigenvalues is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The resulting pencil `Acl-λEcl := Q'*(A+K*C-λ(E+L*C))*Z`,  where `Q` and `Z` are the   orthogonal/unitary matrices used to obtain the pair `(Acl,Ecl)` in a generalized Schur form (GSF), has the form

```
            ( Afu-λEfu    *        *     )     
 Acl-λEcl = (   0      Aia-λEia    *     )  
            (   0         0     Aig-λEig )
```

where: `Afu-λEfu`, with the pair `(Afu,Efu)` in a generalized Schur form,  contains `nfu` fixed (unobservable) finite eigenvalues of `A-λE`, `Aia-λEia`, with `Aia` upper triangular and invertible and `Eia` upper triangular and nilpotent, contains `nia` assigned infinite generalized eigenvalues;  `Aig-λEig`, with `Aig` upper triangular and invertible and `Eig` upper triangular and nilpotent, contains the `ninf` infinite eigenvalues of `A-λE`.  The matrices `Acl`, `Ecl`, `Q`, `Z` and the vectors `α` and `β` such that `α./β` are the generalized eigenvalues of  the pair `(Acl,Ecl)` are returned in the `GeneralizeSchur` object `Scl`.  The values of `nfu`, `nia` and `ninf` and are returned in the 3-dimensional vector `blkdims = [nfu, nia, ninf]`.

Method:  For a general pair `(A-λE,C)` the dual of the modified generalized Schur method of [1] is used to determine `K` and `L` such that the pair `(A+K*C,E+L*G)` has only infinite eigenvalues.

References:

[1] A. Varga.      On stabilization methods of descriptor systems.     Systems & Control Letters, vol. 24, pp.133-138, 1995.
