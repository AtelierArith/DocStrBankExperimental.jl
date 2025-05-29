```
salocd(A, C; evals, sdeg, disc = false, atol1 = 0, atol2 = 0, rtol) -> (K, Scl, blkdims)
```

Compute for the pair `(A,C)`, a matrix `K` such that all eigenvalues of the matrix `A+K*C` lie in the stability domain `Cs`  specified by the stability degree parameter `sdeg` and stability type parameter `disc`.  If `disc = false`, `Cs` is the set of complex numbers with real parts at most `sdeg`, while if `disc = true`,  `Cs` is the set of complex numbers with moduli at most `sdeg` (i.e., the interior of a disc of radius `sdeg` centered in the origin).  `evals` is a real or complex vector, which contains the desired eigenvalues of the matrix `A+K*C` within `Cs`.  For real data `A` and `C`, `evals` must be a self-conjugated complex set to ensure that the resulting `K` is also a real matrix. 

For a pair `(A,C)` with `A` of order `n`, the number of assignable eigenvalues is `nc := n-nu`,   where `nu` is the number of fixed eigenvalues of `A`. The assignable eigenvalues are called the *observable eigenvalues*,  while the fixed eigenvalues are called the *unobservable eigenvalues* (these are the zeros of the pencil `[A-λI; C]`).  The spectrum allocation is achieved by successively replacing the observable eigenvalues of `A` lying outside of the  stability domain `Cs` with eigenvalues provided in `evals`. All eigenvalues of `A` lying in `Cs` are kept unalterred.   If the number of specified eigenvalues in `evals` is less than the number of observable eigenvalues of `A` outside of `Cs` (e.g., if `evals = missing`), then some of the observable eigenvalues of `A` are assigned to the nearest values  on the boundary of `Cs`. If `sdeg = missing` and `evals = missing`, the default value used for `sdeg` is -0.05  if  `disc = false` and 0.95 if `disc = true`. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `C`,   and the relative tolerance for the nonzero elements of `A` and `C`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the machine epsilon of the element type of `A`. 

The resulting matrix `Acl := Z'*(A+K*C)*Z` in a Schur form, where `Z` is the orthogonal/unitary matrix used  to obtain the matrix `A+K*C` in Schur form, has the form

```
       ( Au  *   *  )     
 Acl = ( 0   Aa  *  ) 
       ( 0   0   Ag )
```

where:  `Au` contains `nu` unobservable eigenvalues of `A` lying outside `Cs`,  `Aa` contains the `na` assigned eigenvalues in `Cs` and `Ag` contains the `ng` eigenvalues of `A` in `Cs`.  The matrices `Acl` and `Z` and the vector `α` of eigenvalues of `Acl` (also of `A+K*C`) are returned in the `Schur` object `Scl`.  The values of `nu`, `na` and `ng` are returned in the 3-dimensional vector `blkdims = [nu, na, ng]`.

Method:  The Schur method of [1] is applied to the dual pair `(A',C')` (extended to possibly unobservable pairs).  

References:

[1] A. Varga.      A Schur method for pole assignment.     IEEE Trans. on Automatic Control, vol. 26, pp. 517-519, 1981.
