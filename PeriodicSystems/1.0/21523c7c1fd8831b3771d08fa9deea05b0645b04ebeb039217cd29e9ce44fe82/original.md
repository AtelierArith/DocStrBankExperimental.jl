```
pslinfnorm(psys, hinfnorm = false, rtolinf = 0.001, fast = true, offset = sqrt(ϵ)) -> (linfnorm, fpeak)
pshinfnorm(psys, rtolinf = 0.001, fast = true, offset = sqrt(ϵ)) -> (hinfnorm, fpeak)
```

Compute for a discrete-time periodic system `psys = (A(t),B(t),C(t),D(t)` with the lifted transfer function  matrix `G(λ)`  the `L∞` norm `linfnorm` with `pslinfnorm` or the `H∞` norm `hinfnorm` with `pshinfnorm` (i.e.,  the peak gain of `G(λ)`) and  the corresponding peak frequency `fpeak`, where the peak gain is achieved. If `hinfnorm = true`, the `H∞` norm is computed with `pslinfnorm`.

The `L∞` norm is infinite if `psys` has poles on the stability domain boundary,  i.e., on the unit circle. The `H∞` norm is infinite if `psys` has unstable poles. 

To check the lack of poles on the stability domain boundary, the poles of `psys`  must not have moduli within the interval `[1-β,1+β]`, where `β` is the stability domain boundary offset.   The offset  `β` to be used can be specified via the keyword parameter `offset = β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The keyword argument `rtolinf` specifies the relative accuracy for the computed infinity norm.  The  default value used for `rtolinf` is `0.001`.

The computation of the `L∞` norm is based on the algorithm proposed in [1].  The involved computations of characteristic multipliers are performed either with the fast reduction method of [2],  if `fast = true` or if time-varying dimensions are present,  or the generalized periodic Schur decomposition based method of [3], if `fast = false`.  

*References*

[1] A. Varga. "Computation of L∞-norm of linear discrete-time periodic systems." Proc. MTNS, Kyoto, 2007.

[2] A. Varga and P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems & Control Letters 50:371–381, 2003.

[3] Kressner, D.     An efficient and reliable implementation of the periodic QZ     algorithm. IFAC Workshop on Periodic Control Systems (PSYCO     2001), Como (Italy), August 27-28 2001. Periodic Control     Systems 2001 (IFAC Proceedings Volumes), Pergamon.
