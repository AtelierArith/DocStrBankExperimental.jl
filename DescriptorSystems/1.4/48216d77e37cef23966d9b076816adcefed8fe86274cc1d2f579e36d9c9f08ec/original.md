```
gnehari(sys[, γ]; fast = true, offset = β, 
                atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (sysx, σ1)
```

Compute for the descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)` the optimal or suboptimal Nehari approximation `sysx = (Ax-λEx,Bx,Cx,Dx)`  with the transfer function matrix `X(λ)`. The optimal Nehari approximation  `X(λ)` satisfies

$$
     \| G(\lambda) - X(\lambda) \|_\infty = \| G^{*}_u(\lambda) \|_H := \sigma_1,
$$

where ${\small G_u(\lambda)}$ is the proper antistable part of `G(λ)`. The resulting $σ_1$ is the Hankel-norm of ${\small G^{*}_u(\lambda)}$  (also the L∞-norm of the optimal approximation error).  For a given $γ > σ_1$, the suboptimal approximation satisfies

$$
     \| G(\lambda) - X(\lambda) \|_\infty \leq \gamma .
$$

The Nehari approximation is stable if  `G(λ)` has no poles on the boundary of the stability domain  `Cs`. In the continuous-time, `Cs` is the set of complex numbers with negative real parts and its boundary  is the extended imaginary axis (containig also the poit at infinity), while, in the discrete-time case, `Cs` is the set complex number with moduli less than one and its boundary is the unit circle centered in the origin. 

To assess the presence of poles in `Cs`, a boundary offset  `β`  can be specified via the keyword parameter `offset = β`.  Accordingly, for a continuous-time system, the stable poles in   `Cs` have real parts less than or equal to `β`,  while for a discrete-time system, they have moduli less than or equal to 1+β`.  The default value used for`β`is`sqrt(ϵ)`, where`ϵ`is the working machine precision.  For a negative values of`β`(e.g.,`β = -sqrt(ϵ)`), an extended stability domain corresponding to the closure of`Cs`is used instead of`Cs`. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance  for the nonzero elements of `A` and `E`. The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sys`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol` and `atol2 = atol`. 

The separation of the finite and infinite eigenvalues is performed using  rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Method:* Let `G(λ) = Gs(λ) + Gu(λ)` be an additive decomposition of `G(λ)`  such that `Gs(λ)` has only poles in the closure of `Cs` (or its closure if `β < 0`)  and `Gu(λ)` is the antistable part having only  unstable poles.   The Hankel-norm approximation methods of [1] and [2],  with extensions for descriptor systems, are used to compute a stable Nehari approximation `Gn(λ)` of the unstable part `Gu(λ)` and the resulting solution is computed as `X(λ) = Gs(λ) + Gn(λ)`.

*References:*

[1] K. Glover. All optimal Hankel-norm approximations of linear        multivariable systems and their L∞ error bounds,        Int. J. Control, vol. 39, pp. 1115-1193, 1984.

[2] M. G. Safonov, R. Y. Chiang, and D. J. N. Limebeer.         Optimal Hankel model reduction for nonminimal systems.         IEEE Trans. Automat. Control, vol. 35, pp. 496–502, 1990.
