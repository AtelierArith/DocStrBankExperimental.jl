```
gsklf(A, E, B, C, D; disc = false, jobopt = "none", offset = sqrt(ϵ), fast = true, atol1 = 0, atol2 = 0, rtol, 
     withQ = true, withZ = true) -> (F, G, Q, Z, dimsc, nmszer, nizer)
```

Reduce the structured matrix pencil `M - λN` 

```
           | A-λE | B | 
  M - λN = |------|---|
           |  C   | D |
```

with the `n x n` pencil `A-λE` regular and `[E B]` of full row rank `n`,  to an equivalent form `F - λG = diag(Q',I)*(M - λN)*Z` using orthogonal or unitary transformation  matrices `Q` and `Z` such that the transformed matrices `F` and `G` are in the following special, row partition preserving, Kronecker-like form

```
            | Ar-λEr    *     *   *   |
            |   0     Al-λEl  Bl  *   |
   F - λG = |   0       0     0   Bn  | ,    
            |-------------------------|
            |   0       Cl    Dl  *   |
```

where: (1) `Ar-λEr` is a `mr x nr` full row rank pencil, which contains the right Kronecker structure        of `M - λN` and that part of its zeros which lie outside of the domain of interest `Cb` of       the complex plane defined by the keyword arguments `disc` and `jobopt`;  (2)  `Al-lambda*El` is an `nl x nl` regular square pencil with `El` invertible and upper triangular; (3)  `Bl` is an `nl x ml` matrix, where `ml` is the normal rank       of the transfer function matrix `C*inv(λE-A)*B+D`;  (4)  `Bn` is an invertible matrix of order `nsinf`. 

The column dimensions `(nr, nl, ml, nsinf)` are returned in `dimsc`. 

The full column rank subpencil 

```
            | Al-λEl | Bl | 
Ml - λNl := |--------|----|
            |   Cl   | Dl |
```

contains the left Kronecker structure of `M - λN` and its zeros lying in the domain of interest `Cb`, and has the property that `rank [Al-λEl Bl] = nl` provided `rank [A-λE B] = n` for all finite `λ ∈ Cb`    (finite stabilizability with respect to `Cb`).  The number of finite zeros lying on the boundary of `Cb`, if available, is returned in `nmszer`,  otherwise `nmszer` is set to `missing`.   If `disc = false`, the number of infinite zeros, if available, is returned in `nizer`,  otherwise `nizer` is set to `missing`. If `disc = true`, `nizer` is set to 0.  The boundary offset  `β` to be used to assess the zeros on the boundary of `Cb` is specified  by the keyword parameter `offset`. Accordingly, if `disc = false`, then the boundary of `Cb` contains the complex numbers with real parts within the interval `[-β,β]`, while if `disc = true`,  then the boundary of `Cb` contains the complex numbers with moduli within the interval `[1-β,1+β]`. The default value used for `β` is `sqrt(ϵ)`  (the machine precision of the element type of `A`). 

The domain of interest `Cb` for the zeros of the pencil `Ml - λNl` is defined as follows:

if `jobopt = none`, then `Cb` is the empty set and no zeros of `M - λN` are included in `Ml - λNl`;

if  `jobopt = all`, then `Cb` is the extended complex plane (including infinity) and     all zeros of `M - λN` are included in `Ml - λNl`;

if `jobopt = finite`, then `Cb` is the complex plane (without infinity) and     all finite zeros of `M - λN` are included in `Ml - λNl`;

if `jobopt = infinite`, then `Cb` is the point at infinity and     all infinite zeros of `M - λN` are included in `Ml - λNl`;

if `jobopt = stable`, then, for `disc = false`, `Cb` is the set of complex numbers     with real parts less than `-β`, while for `disc = true`, `Cb` is the set of complex numbers     with moduli less than `1-β` and all finite zeros of `M - λN` in `Cb` are included in `Ml - λNl`;

if `jobopt = unstable`, then, for `disc = false`, `Cb` is the set of complex numbers     with real parts greater than `β` or infinite, while for `disc = true`, `Cb` is the set of complex numbers     with moduli greater than `1+β` or infinite and all finite and infinite zeros of `M - λN` in `Cb` are included in `Ml - λNl`;

if `jobopt = s-unstable`, then, for `disc = false`, `Cb` is the set of complex numbers     with real parts greater than `-β` or infinite, while for `disc = true`, `Cb` is the set of complex numbers     with moduli greater than `1-β` or infinite and all finite and infinite zeros of `M - λN` in `Cb` are included in `Ml - λNl`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`,  and the relative tolerance  for the nonzero elements of `M` and `N`.  The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the `n x n` matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  

Method: The reduction algorithm of [1] has been adapted to deal with several zero selection options. 

References

[1] Oara, C.      Constructive solutions to spectral and inner–outer factorizations      with respect to the disk. Automatica, 41:1855–1866, 2005.
