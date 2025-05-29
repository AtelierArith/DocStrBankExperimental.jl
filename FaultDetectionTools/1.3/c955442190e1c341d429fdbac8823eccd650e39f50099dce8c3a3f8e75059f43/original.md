```
 mddist2c(sysm1, sysm2; MDfreq, cdinp = false, distance = "nugap", 
          rtolinf = 0.00001, offset, atol, atol1 = atol, atol2 = atol, rtol = 0, fast = true) -> (dist, fpeak)
```

Compute the pairwise distances between two sets of multiple component synthesis models  `sysm1::MDMModel` and `sysm2::MDMModel`.   If `sysm1` contains `N` component models and `sysm2` contains `M` component models,  then the resulting `dist` and `fpeak` are `N × M` real matrices, whose `[i,j]`-th entries contain the  distance beetwen the systems `sysm1.sys[i]` and `sysm2.sys[j]`, and, respectively,  the corresponding peak frequency for which the value of the computed distance is achieved.   Both `sysm1` and  `sysm2` can be alternatively specified as vectors of component synthesis models. 

The `i`-th component system `sysm1.sys[i]` has a descriptor realization of the form  `sysm1.sys[i] = (A1i-λE1i,B1i,C1i,D1i)` and the corresponding input-output form is

```
  y1i = Gu1i(λ)*u + Gd1i(λ)*di + Gw1i(λ)*wi + Gv1i(λ)*vi
```

with the Laplace- or Z-transformed plant outputs `y1i`, control inputs `u`,  disturbance inputs `di`, noise inputs `wi`, and auxiliary inputs `vi`,   and with `Gu1i(λ)`, `Gd1i(λ)`, `Gw1i(λ)` and  `Gv1i(λ)`, the corresponding transfer function matrices. Similarly,  the `j`-th component system `sysm2.sys[j]` has a descriptor realization of the form  `sysm2.sys[j]= (A2j-λE2j,B2j,C2j,D2j)` and the corresponding input-output form is

```
  y2j = Gu2j(λ)*u + Gd2j(λ)*dj + Gw2j(λ)*wj + Gv2j(λ)*vj
```

with the Laplace- or Z-transformed plant outputs `y2j`, control inputs `u`,  disturbance inputs `dj`, noise inputs `wj`, and auxiliary inputs `vj`,   and with `Gu2j(λ)`, `Gd2j(λ)`, `Gw2j(λ)` and  `Gv2j(λ)`, the corresponding transfer function matrices. 

The distance beetwen the systems `sysm1.sys[i]` and `sysm2.sys[j]` is evaluated as

```
  dist[i,j] = distf(G1i(λ),G2j(λ)),
```

where `distf(⋅,⋅)` is a distance function specified via the option parameter `distance` (see below) and `G1i(λ)` and `G2j(λ)` are suitably defined transfer function matrices  via the option parameter `cdinp` (see below). The corresponding peak frequency `fpeak[i,j]` is the frequency value for which the distance is achieved.

`distance = job` specifies the distance function to be used as follows:

```
job = "nugap"  - use the ν-gap distance ν(G1i(λ),G2j(λ)) defined in [1] (default)
job = "inf"    - use the H∞-norm of the difference (i.e., ||G1i(λ)-G2j(λ)||_∞)
job = "2"      - use the H2-norm of the difference (i.e., ||G1i(λ)-G2j(λ)||_2)
```

If `cdinp = false` (default), then `G1i(λ) = Gu1i(λ)` and `G2j(λ) = Gu2j(λ)`, while if `cdinp = true` then `G1i(λ) = [Gu1i(λ) Gd1i(λ)]` and `G2j(λ) = [Gu2j(λ) Gd2j(λ)]`.  If `Gd1i(λ)` has less columns than `Gd2j(λ)`, then `[Gd1i(λ) 0]` (with suitably padded zero columns)  is used instead `Gd1i(λ)`, while  if `Gd1i(λ)` has more columns than `Gd2j(λ)`, then `[Gd2j(λ) 0]` is used instead `Gd2j(λ)`.

If `MDfreq = ω`, where `ω` is a vector of real frequency values, then each distance `dist[i,j]`  is the maximum of pointwise distances evaluated for all frequencies in `ω` and  the corresponding frequency `fpeak[i,j]` is the value for which the maximum pointwise distance is achieved.

The stability boundary offset, `β`, to be used to assess the finite poles/zeros which belong to the boundary of the stability domain can be specified via the keyword parameter `offset = β`. Accordingly, for a continuous-time system, these are the finite poles/zeros having  real parts within the interval `[-β,β]`, while for a discrete-time system,  these are the finite pole/zeros having moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

Pencil reduction algorithms are employed to compute range and coimage spaces involved in evaluating  the ν-gap or the H∞-norm distances. These algorithms perform rank decisions based on rank  revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of the state-space matrices     `A1i`, `A2j`, `B1i`, `B2j`, `C1i`, `C2j`, `D1i` and `D2j`, the absolute tolerance for the nonzero elements of `E1i` and `E2j`,    and the relative tolerance for the nonzero elements of all above matrices.   The default relative tolerance is `nij*ϵ`, where `ϵ` is the working machine epsilon  and `nij` is the maximum of the orders of the systems `sysm1.sys[i]` and `sysm2.sys[j]`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol`, `atol2 = atol`. 

The keyword argument `rtolinf = tol` specifies the relative accuracy `tol` to be used  to compute infinity norms. The default value used is `tol = 0.00001`.

*Method:* The evaluation of ν-gap uses the definition proposed in [1], extended to generalized LTI (descriptor) systems. 

*References:*

[1] G. Vinnicombe. Uncertainty and feedback: H∞ loop-shaping and the ν-gap metric.      Imperial College Press, London, 2001. 
