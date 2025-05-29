```
 mdperf(sysR::MDFilterIF; MDfreq, cdinp = false, rtolinf = 0.00001, 
        offset, atol, atol1 = atol, atol2 = atol, rtol = 0, fast = true) -> (mdgain, fpeak)
```

Compute the distance-mapping performance of a collection of model detection filters using the model detection filter internal form object `sysR::MDFilterIF`.   For an `M × N` array of filters `sysR`, the `M × N` arrays of model detection performance gains  `mdgain` and the corresponding peak frequencies `fpeak` are determined as follows.  Let the `(i,j)`-th component filter `sysR.sys[i,j]` have the input-output form

```
 rij = Ruij(λ)*u + Rdij(λ)*dj + Rwij(λ)*wj + Rvij(λ)*vj ,
```

with the Laplace- or Z-transformed residual output `rij`, control inputs `u`,  disturbance inputs `dj`, noise inputs `wj`, and auxiliary inputs `vj`,   and with `Ruij(λ)`, `Rdij(λ)`, `Rwij(λ)` and `Rvij(λ)`, the corresponding transfer function matrices.  Then, the `(i,j)`-th performance gain is evaluated as  `mdgain[i,j] = ||Ruij(λ)||∞` if `cdinp = false` (default) or `mdgain[i,j] = ||[Ruij(λ) Rdij(λ)]||∞` if `cdinp = true`  and `fpeak[i,j]` contains the corresponding peak frequency. 

If `MDfreq = ω`, where `ω` is a given vector of real frequency values, then each gain `mdgain[i,j]` represents the maximum of 2-norm pointwise gains evaluated for all frequencies in `ω` and  `fpeak[i,j]` is the corresponding peak frequency.

The stability boundary offset, `β`, to be used to assess the finite poles which belong to the boundary of the stability domain can be specified via the keyword parameter `offset = β`. Accordingly, for a continuous-time system, these are the finite poles having  real parts within the interval `[-β,β]`, while for a discrete-time system,  these are the finite pole having moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

Pencil reduction algorithms are employed to compute the H∞-norms.  These algorithms perform rank decisions based on rank  revealing QR-decompositions with column pivoting  if `fast = true` (default) or the more reliable SVD-decompositions if `fast = false`.

If `(Arij-λErij,Brij,Crij,Drij)` is the descriptor realization of `sysR.sys[i,j]`, then  the keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Arij`, `Brij`, `Crij`, `Drij`, the absolute tolerance for the nonzero elements of `Erij`,   and the relative tolerance for the nonzero elements of `Arij`, `Brij`, `Crij`, `Drij` and `Eirj`. The default relative tolerance is `nij*ϵ`, where `ϵ` is the working *machine epsilon*  and `nij` is the order of the system `sysR.sys[i,j]`.   The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 

The keyword argument `rtolinf = tol` specifies the relative accuracy `tol` to be used  to compute the infinity norms. The default value used is `tol = 0.00001`.
