```
goifac(sys; atol = 0, atol1 = atol, atol2 = atol, atol3 = atol, rtol, 
       fast = true, minphase = true, offset = sqrt(ϵ)) -> (sysi, syso, info)
```

Compute for the descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`,  the square inner factor `sysi = (Ai-λEi,Bi,Ci,Di)` with the transfer function matrix `Gi(λ)`  and the minimum-phase quasi-outer factor or the full column rank factor `syso = (Ao-λEo,Bo,Co,Do)`  with the transfer function matrix `Go(λ)` such that

```
 G(λ) = Go(λ)*Gi[1:r,:](λ)    (*),
```

where `r` is the normal rank of `G(λ)`. The resulting proper and stable inner factor satisfies  `Gi'(λ)*Gi(λ) = I`. If `sys` is stable (proper), then the resulting `syso` is stable (proper).  The resulting factor `Go(λ)` has full column rank `r`. Depending on the selected factorization option, if `minphase = true`, then `Go(λ)` is minimum phase,  excepting possibly zeros on the  boundary of the appropriate stability domain `Cs`, or if `minphase = false`, then `Go(λ)`  contains all zeros of `G(λ)`, in which case (*) is the extended RQ-like factorization of `G(λ)`. For a continuous-time system `sys`, the stability domain `Cs` is defined as the set of  complex numbers with real parts at most `-β`,  while for a discrete-time system `sys`, `Cs` is the set of complex numbers with  moduli at most `1-β` (i.e., the interior of a disc of radius `1-β` centered in the origin).  The boundary offset  `β` to be used to assess the stability of zeros and their number  on the boundary of `Cs` can be specified via the keyword parameter `offset = β`. Accordingly, for a continuous-time system,  the boundary of `Cs` contains the complex numbers with real parts within the interval `[-β,β]`,  while for a discrete-time system, the boundary of `Cs` contains the complex numbers with moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The resulting named triple `info` contains `(nrank, nfuz, niuz)`, where `info.nrank = r`,  the normal rank of `G(λ)`, `info.nfuz` is the number of finite zeros of `syso` on  the boundary of `Cs`, and `info.niuz` is the number of infinite zeros of `syso`.  `info.nfuz` is set to `missing` if `minphase = false`. 

*Note:* `syso` may generally contain a *free inner factor*, which can be eliminated by  removing the finite unobservable eigenvalues. 

The keyword arguments `atol1`, `atol2`, `atol3`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A` and `C`,  the absolute tolerance for the nonzero elements of `E`,  the absolute tolerance for the nonzero elements of `B` and `D`,   and the relative tolerance for the nonzero elements of `A`, `E`, `B`, `C` and `D`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sys`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol`, `atol3 = atol`. 

For the assessment of zeros, the dual system pencil `transpose([A-λE B; C D])` is reduced to a  special Kronecker-like form (see [2]). In this reduction, the  performed rank decisions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Method:*  For a continuous-time system, the dual system is formed and the factorization algorithm  of [1] is used, while for a discrete-time system, the factorization algorithm of [1] is used.

*References:*

[1] C. Oara and A. Varga.     Computation of the general inner-outer and spectral factorizations.     IEEE Trans. Autom. Control, vol. 45, pp. 2307–2325, 2000.

[2] C. Oara.     Constructive solutions to spectral and inner–outer factorizations      respect to the disk. Automatica,  41, pp. 1855–1866, 2005. 
