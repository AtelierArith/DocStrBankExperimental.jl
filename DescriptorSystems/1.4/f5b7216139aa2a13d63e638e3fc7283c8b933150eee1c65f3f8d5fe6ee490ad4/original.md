```
glinfnorm(sys, hinfnorm = false, rtolinf = 0.001, fast = true, offset = sqrt(ϵ), atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (linfnorm, fpeak)
```

Compute for a descriptor system `sys = (A-λE,B,C,D)` with the transfer function  matrix `G(λ)`  the `L∞` norm `linfnorm` (i.e.,  the peak gain of `G(λ)`) and  the corresponding peak frequency `fpeak`, where the peak gain is achieved.  The `L∞` norm is infinite if `G(λ)` has poles on the stability domain boundary,  i.e., on the extended imaginary axis, in the continuous-time case,  or on the unit circle, in the discrete-time case.  If the pencil `A-λE` has uncontrollable and/or unobservable eigenvalues on the boundary of the stability domain, then a reduced order realization is determined first (see below) to eliminate these eigenvalues. 

To check the lack of poles on the stability domain boundary, the eigenvalues of the pencil `A-λE`  must not have real parts in the interval `[-β,β]` for a continuous-time system or  must not have moduli within the interval `[1-β,1+β]` for a discrete-time system, where `β` is the stability domain boundary offset.   The offset  `β` to be used can be specified via the keyword parameter `offset = β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The keyword argument `rtolinf` specifies the relative accuracy for the computed infinity norm.  The  default value used for `rtolinf` is `0.001`.

If `hinfnorm = true`, the `H∞` norm is computed.  In this case, the stability of the zeros of `A-λE` is additionally checked and  the `H∞` norm is infinite for an unstable system. To check the stability, the eigenvalues of the pencil `A-λE` must have real parts less than `-β` for a continuous-time system or  have moduli less than `1-β` for a discrete-time system.

For a continuous-time system `sys` with `E` singular, a reduced order realization is determined first, without  uncontrollable and unobservable finite and infinite eigenvalues of the pencil `A-λE`.  For a discrete-time system or for a system with invertible `E`, a reduced order realization is determined first, without  uncontrollable and unobservable finite eigenvalues of the pencil `A-λE`. The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.   

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.  The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon   and `n` is the order of the system `sys`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
