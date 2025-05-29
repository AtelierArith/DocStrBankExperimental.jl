```
glinfldp(sys1, sys2, [, γ]; nehari = false, reltol = 0.0001, fast = true, offset = β, 
         atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (sysx, mindist)
```

Determine for the descriptor systems `sys1 = (A1-λE1,B1,C1,D1)` and  `sys2 = (A2-λE2,B2,C2,D2)` with the transfer function matrices $G_1(λ)$ and $G_2(λ)$,  respectively, the descriptor system `sysx` with the transfer function matrix $X(λ)$  such that $X(λ)$ is the solution of the 2-block `L∞` *least distance problem* (`LDP`)

$$
      \text{mindist} := \min \|G_1(λ)-X(λ) \mid   G_2(λ) \|_\infty 
$$

`mindist` is the achieved minimum distance corresponding to the optimal solution.  If `sys2 = []`, an 1-block `LDP` is solved.  `sys1` and `sys2` must not have poles on the boundary of the stability domain `Cs`. It is assumed that `sys2` has no poles on the boundary of the stability domain (see below). The resulting solution is stable, provided `sys1` has no poles on the boundary  of the stability domain as well. 

If  ${\small γ > \|G_2(λ)\|_\infty}$ is a desired sub-optimality degree, then the  `γ`-suboptimal `LDP` 

$$
     \text{mindist} := \|G_1(λ)-X(λ) \mid G_2(λ) \|_\infty < γ
$$

is solved and `mindist` is the achieved suboptimal distance.

The call with

```
glinfldp(sys[, m2[, γ]]; nehari = false, fast = true, offset = β, 
         atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (sysx, mindist)
```

uses the compound descriptor system `sys = (A-λE,[B1 B2],C,[D1 D2])`,  where `B2` has `m2` columns, to define   the descriptor systems `sys1 = (A-λE,B1,C,D1)` and `sys2 = (A-λE,B2,C,D2)` (i.e., `A1-λE1 = A2-λE2 = A-λE` and `C1 = C2 = C`).  If `m2 = 0`, an 1-block `LDP` is solved.  `sys2` must not have poles on the boundary of the stability domain `Cs`.

If `nehari = true`, the optimal or suboptimal Nehari approximation is used to solve the `LDP`. If `nehari = false` (default), the optimal solution is computed using the `γ`-iteration [1]. 

The keyword argument `reltol` specifies the relative tolerance for the desired accuracy of `γ`-iteration.  The iterations are performed until the current estimations of maximum $γ_u$ and minimum $γ_l$ of   the optimal distance $γ_o$, $γ_l \leq γ_o \leq γ_u$, satisfies 

$$
     γ_u-γ_l \leq \text{reltol} * \text{gap} ,
$$

where `gap` is the original gap (internally determined).

To assess the presence of poles on the boundary of the stability domain `Cs`, a boundary offset  `β`  can be specified via the keyword parameter `offset = β`.  Accordingly, for a continuous-time setting,  the boundary of `Cs` contains the complex numbers with real parts within the interval `[-β,β]`,  while for a discete-time setting, the boundary of `Cs` contains the complex numbers with moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance  for the nonzero elements of `A` and `E`. The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sys`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol` and `atol2 = atol`. 

The rank decisions in the underlying pencil manipulation algorithms are  based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Method:* The approach of [1] is used for the solution of the 2-block least distance problem. Necessary conditions for solvability of the LDP with a stable solution is that `sys1` and `sys2` have no poles  on the boundary of the stability domain `Cs`.

*References:* [1] C.-C. Chu, J. C. Doyle, and E. B. Lee     The general distance problem in H∞  optimal control theory,     Int. J. Control, vol 44, pp. 565-596, 1986.
