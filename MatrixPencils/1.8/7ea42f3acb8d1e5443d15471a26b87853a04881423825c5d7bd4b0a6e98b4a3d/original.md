```
saloc(A, E, B; evals, sdeg, disc = false, atol1 = 0, atol2 = 0, atol3 = 0, rtol, sepinf = true, fast = true) -> (F, Scl, blkdims)
```

Compute for the pair `(A-λE,B)`, with `A-λE` a regular pencil, a matrix `F` such that all finite eigenvalues of the  pencil `A+B*F-λE` lie in the stability domain `Cs` specified by the stability degree parameter `sdeg` and stability type parameter `disc`.  If `disc = false`, `Cs` is the set of complex numbers with real parts at most `sdeg`, while if `disc = true`,  `Cs` is the set of complex numbers with moduli at most `sdeg` (i.e., the interior of a disc of radius `sdeg` centered in the origin).  `evals` is a real or complex vector, which contains a set of finite desired eigenvalues for the pencil `A+B*F-λE`.  For real data `A`, `E`, and `B`, `evals` must be a self-conjugated complex set to ensure that the resulting `F` is also a real matrix. 

For a pair `(A-λE,B)` with `A` of order `n`, the number of assignable finite eigenvalues is `nfc := n-ninf-nfu`,   where `ninf` is the number of infinite eigenvalues of `A-λE` and `nfu` is the number of fixed finite eigenvalues of `A-λE`.  The assignable finite eigenvalues are called the *controllable finite eigenvalues*,  while the fixed finite eigenvalues are called the *uncontrollable finite eigenvalues* (these are the finite zeros of the pencil `[A-λE B]`).  The spectrum allocation is achieved by successively replacing the controllable finite eigenvalues of `A-λE` lying outside of the  stability domain `Cs` with eigenvalues provided in `evals`. All finite eigenvalues of `A-λE` lying in `Cs` are kept unalterred.   If the number of specified eigenvalues in `evals` is less than the number of controllable finite eigenvalues of `A-λE` outside of `Cs` (e.g., if `evals = missing`), then some of the controllable finite eigenvalues of `A-λE` are assigned to the nearest values  on the boundary of `Cs`. If `sdeg = missing` and `evals = missing`, the default value used for `sdeg` is -0.05  if  `disc = false` and 0.95 if `disc = true`. 

The keyword arguments `atol1`, `atol2`, `atol3`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`, the absolute tolerance for the nonzero elements of `B`,   and the relative tolerance for the nonzero elements of `A`, `E` and `B`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the machine epsilon of the element type of `A`. 

The keyword argument `sepinf` specifies the option for a preliminary separation  of the infinite eigenvalues of the pencil `A-λE` as follows: if `sepinf = false`, no separation of infinite eigenvalues is performed,  while for `sepinf = true` (the default option), a preliminary separation of the infinite eigenvalues from the finite ones is performed. If `E` is nonsingular, then `sepinf = false` is recommended to be used. If `E` is numerically singular, then the option `sepinf = false` is used.  The separation of finite and infinite eigenvalues is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The resulting pencil `Acl-λEcl := Q'*(A+B*F-λE)*Z`,  where `Q` and `Z` are the   orthogonal/unitary matrices used to obtain the pair `(Acl,Ecl)` in a generalized Schur form (GSF), has the form

```
            ( Ai-λEi    *        *       *      )     
 Acl-λEcl = (   0    Afg-λEfg    *       *      )  
            (   0       0     Afa-λEfa   *      )    
            (   0       0        0     Afu-λEfu )
```

where: `Ai-λEi` with `Ai` upper triangular and invertible and `Ei` upper triangular and nilpotent, contains the `ninf` infinite eigenvalues of `A-λE`;  `Afg-λEfg` contains `nfg` finite eigenvalues of `A-λE` in `Cs`; `Afa-λEfa` contains `nfa` assigned finite generalized eigenvalues in `Cs`;  and `Afu-λEfu` contains `nfu` uncontrollable finite eigenvalues of `A-λE` lying outside `Cs`.  The matrices `Acl`, `Ecl`, `Q`, `Z` and the vectors `α` and `β` such that `α./β` are the generalized eigenvalues of  the pair `(Acl,Ecl)` are returned in the `GeneralizeSchur` object `Scl`.  The values of `ninf`, `nfg`, `nfa` and `nfu` are returned in the 4-dimensional vector `blkdims = [ninf, nfg, nfa, nfu]`.

Method:  For a pair `(A-λE,B)` with `E = I`, the Schur method of [1] is used, while for a general pair `(A-λE,B)` the generalized Schur method of [2]  is used to solve the R-stabilzation problem.

References:

[1] A. Varga.      A Schur method for pole assignment.     IEEE Trans. on Automatic Control, vol. 26, pp. 517-519, 1981.

[2] A. Varga.      On stabilization methods of descriptor systems.     Systems & Control Letters, vol. 24, pp.133-138, 1995.
