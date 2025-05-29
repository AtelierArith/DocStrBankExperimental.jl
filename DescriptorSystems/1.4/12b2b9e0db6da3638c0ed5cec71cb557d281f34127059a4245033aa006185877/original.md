```
gnrcf(sys; fast = true, ss = false, 
     atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (sysn, sysm)
```

Compute for the descriptor system `sys = (A-λE,B,C,D)`, the factors  `sysn = (An-λEn,Bn,Cn,Dn)` and `sysm = (An-λEn,Bn,Cm,Dm)` of its normalized right coprime factorization. If `sys`, `sysn` and `sysm`   have the transfer function matrices `G(λ)`, `N(λ)` and `M(λ)`, respectively, then `G(λ) = N(λ)*inv(M(λ))`, with `N(λ)` and `M(λ)` proper and stable transfer  function matrices and `[N(λ);M(λ)]` inner. The resulting `En = I` if `ss = true`. 

Pencil reduction algorithms are employed which perform rank decisions based on rank  revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C` and `D`, the absolute tolerance for the nonzero elements of `E`,    and the relative tolerance for the nonzero elements of `A`, `E`, `B`, `C` and `D`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the machine epsilon of the element type of `A`  and `n` is the order of the system `sys`. The keyword argument `atol` can be used to simultaneously set `atol1 = atol`, `atol2 = atol`.

*Method:* Pencil reduction algorithms are employed to determine the inner range space `R(λ)` of the  transfer function matrix `[G(λ); I]` using the method described in [1], which is based on  the reduction algorithm of [2]. Then the factors `N(λ)` and `M(λ)` result from the partitioning of `R(λ)` as `R(λ) = [N(λ);M(λ)]`. 

*References:*

[1] Varga, A.     A note on computing the range of rational matrices.      arXiv:1707.0048, [https://arxiv.org/abs/1707.0048](https://arxiv.org/abs/1707.004), 2017.

[2] C. Oara.     Constructive solutions to spectral and inner–outer factorizations      respect to the disk. Automatica,  41, pp. 1855–1866, 2005. 
