```
grcf(sys; smarg, sdeg, evals, mindeg = false, mininf = false, fast = true, 
     atol = 0, atol1 = atol, atol2 = atol, atol3 = atol, rtol = n*ϵ) -> (sysn, sysm)
```

Compute for the descriptor system `sys = (A-λE,B,C,D)`, the factors  `sysn = (An-λEn,Bn,Cn,Dn)` and `sysm = (Am-λEm,Bm,Cm,Dm)` of its stable and proper right coprime factorization. If `sys`, `sysn` and `sysm`   have the transfer function matrices `G(λ)`, `N(λ)` and `M(λ)`, respectively, then `G(λ) = N(λ)*inv(M(λ))`, with `N(λ)` and `M(λ)` proper and stable transfer  function matrices.  The resulting matrix pairs `(An,En)` and `(Am,Em)` are in (generalized) Schur form.  The stability domain `Cs` of poles is defined by  the keyword argument `smarg` for the stability margin, as follows:  for a continuous-time system `sys`, `Cs` is the set of complex numbers  with real parts at most `smarg < 0`,  while for a discrete-time system `sys`, `Cs` is the set of complex numbers with  moduli at most `smarg < 1` (i.e., the interior of a disc of radius `smarg` centered in the origin).  If `smarg` is missing, then the employed default values are `smarg = -sqrt(eps)`  for a continuous-time system and `smarg = 1-sqrt(eps)` for a discrete-time system. 

The keyword argument `sdeg` specifies the prescribed stability degree for the  assigned eigenvalues of the factors. If both `sdeg` and `smarg` are missing,  then the employed  default values are `sdeg = -0.05` for a continuous-time system and  `sdeg = 0.95` for a discrete-time system, while if `smarg` is specified,  then `sdeg = smarg` is used. 

The keyword argument `evals` is a real or complex vector, which contains a set  of finite desired eigenvalues for the factors.  For a system with real data, `evals` must be a self-conjugated complex set  to ensure that the resulting factors are also real. 

If `mindeg = false`, both factors `sysn` and `sysm` have descriptor realizations with the same order and with `An = Am`, `En = Em` and `Bn = Bm`. If `mindeg = true`,  the realization of `sysm` is minimal. The number of (finite) poles of `sysm` is  equal to the number of unstable finite poles of `sys`. 

If `mininf = false`, then `An-λEn` and `Am-λEm` may have simple infinite eigenvalues. If `mininf = true`,  then `An-λEn` and `Am-λEm` have no simple infinite eigenvalues. Note that the removing of simple infinite eigenvalues involves matrix inversions. 

The keyword arguments `atol1`, `atol2`, `atol3`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`,  the absolute tolerance for the nonzero elements of `E`,  the absolute tolerance for the nonzero elements of `B`,   and the relative tolerance for the nonzero elements of `A`, `E` and `B`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the machine epsilon of the element type of `A`  and `n` is the order of the system `sys`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol`, `atol3 = atol`.

The preliminary separation of finite and infinite eigenvalues of `A-λE` is performed  using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Method:*  The Procedure GRCF from [2] is implemented, which represents an extension of the recursive factorization approach of [1] to cope with   infinite eigenvalues. All infinite poles are assigned to finite real values.  If `evals` is missing or does not contain a sufficient   number of real values, then a part or all of infinite eigenvalues of `A-λE` are   assigned to the value specified by `sdeg`. The pairs `(An,En)` and `(Am,Em)`  result in *generalized Schur form* with both `An` and `Am` quasi-upper triangular   and `En` and `Em` either both upper triangular or both UniformScalings. 

*References:*

[1] A. Varga. Computation of coprime factorizations of rational matrices.     Linear Algebra and Its Applications, vol. 271, pp.88-115, 1998.

[2] A. Varga. On recursive computation of coprime factorizations of rational matrices.      arXiv:1703.07307, https://arxiv.org/abs/1703.07307, 2020. (to appear in Linear Algebra and Its Applications)
