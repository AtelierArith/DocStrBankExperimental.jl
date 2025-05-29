```
glasol(sysg, sysf[, γ]; L2sol = false, nehari = false, reltol = 0.0001, mindeg = false, poles, sdeg, 
       fast = true, offset = β, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (sysx, info)
```

Determine for the descriptor systems `sysg = (Ag-λEg,Bg,Cg,Dg)` and  `sysf = (Af-λEf,Bf,Cf,Df)` with the transfer function matrices `G(λ)` and `F(λ)`,  respectively, the descriptor system `sysx` with the transfer function matrix `X(λ)`  such that `X(λ)` is the approximate solution of the linear rational equation `X(λ)G(λ) = F(λ)`, which achieves the minimum error norm ${\small \text{mindist} := \min \|X(λ)G(λ) - F(λ)\|}$.  The resulting `X(λ)` has all poles stable or lying on the boundary of the stability domain `Cs`.  If `L2sol = false` (default) then the `L∞`-norm optimal solution is computed, while if `L2sol = true` the `L2`-norm optimal solution is computed.  `sysg` and `sysf` must not have poles on the boundary of the stability domain `Cs`.

If  `γ > 0` is a desired sub-optimality degree, then the `γ`-suboptimal model-matching problem

$$
     \text{mindist} := \|X(λ)G(λ) - F(λ) \| < γ
$$

is solved and `mindist` is the achieved suboptimal distance.

The call with

```
glasol(sysgf[, pf[, γ]]; L2sol = false, nehari = false, reltol = 0.0001, mindeg = false, poles, sdeg, 
       fast = true, offset = β, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (sysx, info)
```

uses the compound descriptor system `sysgf = (A-λE,B,[Cg; Cf],[Dg; Df])`,  where `Cf` and `Df` have `pf` rows, to define   the descriptor systems `sysg = (A-λE,B,Cg,Dg)` and `sysf = (A-λE,B,Cf,Df)` (i.e., `Ag-λEg = Af-λEf = A-λE` and `Bg = Bf = B`).  `sysgf` must not have poles on the boundary of the stability domain `Cs`.

If `nehari = true`, the optimal or suboptimal Nehari approximation is used to solve the  underlying *least-distance problem* (`LDP`). If `nehari = false` (default), the optimal solution is computed using the `γ`-iteration  in the underlying `LDP` [2]. 

If `mindeg = true`, a minimum order solution is determined (if possible),  while if `mindeg = false` (default) a particular solution of non-minimal order is determined. 

The resulting named tuple `info` contains additional information: `info.nrank` is the normal rank of `G(λ)`,  `info.nl` is the number of freely assignable poles of the solution `X(λ)`,   `info.mindist` is the achieved approximation error norm and  `info.nonstandard` is `true` for a non-standard problem, with `G(λ)`  having zeros on the boundary of the stability domain, and `false` for a standard problem, when `G(λ)` has no zeros on the boundary  of the stability domain.  

The keyword argument `reltol` specifies the relative tolerance for the desired accuracy of  the `γ`-iteration employed to solve the underlying least-distance problem.   The iterations are performed until the current estimations of maximum $γ_u$ and minimum $γ_l$ of   the optimal distance satisfies  ${\small γ_u-γ_l < \text{reltol}* \text{gap}}$, where `gap` is the initial estimation of the error gap.

To assess the presence of poles on the boundary of the stability domain `Cs`, a boundary offset  `β`  can be specified via the keyword parameter `offset = β`.  Accordingly, for a continuous-time setting,  the boundary of `Cs` contains the complex numbers with real parts within the interval `[-β,β]`,  while for a discrete-time setting, the boundary of `Cs` contains the complex numbers with moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The vector `poles` specified as a keyword argument, can be used to specify the desired poles of `sysx` alternatively to or jointly with enforcing a desired stability degree `sdeg` of poles. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `Ag`, `Af`, `A`, `Bg`, `Bf`, `Cg`, `Cf`, `Dg`, `Df`,   the absolute tolerance for the nonzero elements of `Eg`, `Ef`, and the relative tolerance  for the nonzero elements of all above matrices. The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sysg`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol` and `atol2 = atol`. 

The rank decisions in the underlying pencil manipulation algorithms are  based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Method:*  An extension of the approach of [1] to descriptor systems is used.

*References:*

[1]  B. A. Francis. A Course in H-infinity Theory,         Vol. 88 of Lecture Notes in Control and Information Sciences,         Springer-Verlag, New York, 1987.

[2] C.-C. Chu, J. C. Doyle, and E. B. Lee.     The general distance problem in H∞  optimal control theory,     Int. J. Control, vol 44, pp. 565-596, 1986.
