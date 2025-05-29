```
 sysf = grsfg(sys, γ; fast = true, stabilize = true, offset = β, 
              atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ)
```

Compute for the descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)` and ${\small γ > \|G(λ)\|_∞}$, the minimum-phase right spectral factor `sysf = (Af-λEf,Bf,Cf,Df)` with the transfer-function matrix `F(λ)`, such that `F(λ)'*F(λ) = γ^2*I-G(λ)'*G(λ)`. If `stabilize = true` (the default), a preliminary stabilization of `sys` is performed.  In this case, `sys` must not have poles on the imaginary-axis in the continuous-time case or  on the unit circle in the discrete-time case. If `stabilize = false`, then no preliminary stabilization is performed. In this case, `sys` must be stable.

To assess the presence of poles on the boundary of the stability domain `Cs`, a boundary offset  `β`  can be specified via the keyword parameter `offset = β`.  Accordingly, for a continuous-time system,  the boundary of `Cs` contains the complex numbers with real parts within the interval `[-β,β]`,  while for a discrete-time system, then the boundary of `Cs` contains the complex numbers with moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

If `stabilize = true`, a preliminary separation of finite and infinite eigenvalues of `A-λE`is performed  using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2`, `atol3`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`,  the absolute tolerance for the nonzero elements of `E`,  the absolute tolerance for the nonzero elements of `C`,   and the relative tolerance for the nonzero elements of `A`, `E` and `C`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol`, `atol3 = atol`.

*Method:* Extensions of the factorization approaches of [1] are used.

*References:*

[1] K. Zhou, J. C. Doyle, and K. Glover. Robust and Optimal Control. Prentice Hall, 1996.
