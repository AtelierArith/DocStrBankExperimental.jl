```
grcfid(sys; mindeg = false, mininf = false, fast = true, offset = sqrt(ϵ), 
       atol = 0, atol1 = atol, atol2 = atol, atol3 = atol, rtol = n*ϵ) -> (sysni, sysmi)
```

Compute for the descriptor system `sys = (A-λE,B,C,D)`, the factors  `sysni = (Ani-λEni,Bni,Cni,Dni)` and `sysmi = (Ami-λEmi,Bmi,Cmi,Dmi)` of its  right coprime factorization with inner denominator. If `sys`, `sysni` and `sysmi`   have the transfer function matrices `G(λ)`, `N(λ)` and `M(λ)`, respectively, then `G(λ) = N(λ)*inv(M(λ))`, with `N(λ)` and `M(λ)` proper and stable transfer  function matrices and the denominator factor `M(λ)` inner.  The resulting matrix pairs `(Ani,Eni)` and `(Ami,Emi)` are in (generalized) Schur form.  The system `sys` must not have poles on the boundary of the stability domain `Cs`. In terms of eigenvalues, this requires for a continuous-time system, that  `A-λE` must not have controllable eigenvalues on the imaginary axis  (excepting simple infinite eigenvalues), while for a discrete-time system,   `A-λE` must not have controllable eigenvalues on the unit circle centered  in the origin. 

To assess the presence of poles on the boundary of `Cs`, a boundary offset  `β`  can be specified via the keyword parameter `offset = β`.  Accordingly, for a continuous-time system,  the boundary of `Cs` contains the complex numbers with real parts within the interval `[-β,β]`,  while for a discrete-time system, then the boundary of `Cs` contains the complex numbers with moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

If `mindeg = false`, both factors `sysni` and `sysmi` have descriptor realizations with the same order and with `Ani = Ami`, `Eni = Emi` and `Bni = Bmi`. If `mindeg = true`,  the realization of `sysmi` is minimal. The number of (finite) poles of `sysmi` is  equal to the number of unstable finite poles of `sys`. 

If `mininf = false`, then `Ani-λEni` and `Ami-λEmi` may have simple infinite eigenvalues. If `mininf = true`,  then `Ani-λEni` and `Ami-λEmi` have no simple infinite eigenvalues. Note that the removing of simple infinite eigenvalues involves matrix inversions. 

The keyword arguments `atol1`, `atol2`, `atol3`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`,  the absolute tolerance for the nonzero elements of `E`,  the absolute tolerance for the nonzero elements of `B`,   and the relative tolerance for the nonzero elements of `A`, `E` and `B`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol`, `atol3 = atol`.

The preliminary separation of finite and infinite eigenvalues of `A-λE`is performed  using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Method:* An extension of the recursive factorization approach of [1]  is used (see [2] for details). The pairs `(Ani,Eni)` and `(Ami,Emi)` result in *generalized Schur form* with both `Ani` and `Ami` quasi-upper triangular  and `Eni` and `Emi` either both upper triangular or both UniformScalings. 

*References:*

[1] A. Varga. Computation of coprime factorizations of rational matrices.     Linear Algebra and Its Applications, vol. 271, pp.88-115, 1998.

[2] A. Varga. On recursive computation of coprime factorizations of rational matrices.      arXiv:1703.07307, https://arxiv.org/abs/1703.07307, 2020. (to appear in Linear Algebra and Its Applications)
