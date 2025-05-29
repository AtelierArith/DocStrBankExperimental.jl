```
 mddist(sysm; MDfreq, cdinp = false, distance = "nugap",  rtolinf = 0.00001, 
        offset, atol, atol1 = atol, atol2 = atol, rtol = 0, fast = true) -> (dist, fpeak)
```

Compute the pairwise distances between the component models of `sysm::MDMModel`.   If `sysm` contains `N` component models, then the resulting `dist` and `fpeak` are  `N × N` real symmetric matrices, whose `[i,j]`-th elements contain the  distance beetwen the systems `sysm.sys[i]` and `sysm.sys[j]`, and,  respectively, the corresponding `peak frequency` for which the value of the computed distance is achieved.   `sysm` can be alternatively specified as a vector of component synthesis models. 

The `i`-th component system `sysm.sys[i]` has a descriptor realization of the form  `sysm.sys[i] = (Ai-λEi,Bi,Ci,Di)` and the corresponding input-output form is

```
  yi = Gui(λ)*u + Gdi(λ)*di + Gwi(λ)*wi + Gvi(λ)*vi
```

with the Laplace- or Z-transformed plant outputs `yi`, control inputs `u`,  disturbance inputs `di`, noise inputs `wi`, and auxiliary inputs `vi`,   and with `Gui(λ)`, `Gdi(λ)`, `Gwi(λ)` and `Gvi(λ)`, the corresponding transfer function matrices.  

The distance beetwen the systems `sysm.sys[i]` and `sysm.sys[j]` is evaluated as

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

If `cdinp = false` (default), then `G1i(λ) = Gui(λ)` and `G2j(λ) = Guj(λ)`, while if `cdinp = true` then `G1i(λ) = [Gui(λ) Gdi(λ)]` and `G2j(λ) = [Guj(λ) Gdj(λ)]`.  If `Gdi(λ)` has less columns than `Gdj(λ)`, then `[Gdi(λ) 0]` (with suitably padded zero columns)  is used instead `Gdi(λ)`, while  if `Gdi(λ)` has more columns than `Gdj(λ)`, then `[Gdj(λ) 0]` is used instead `Gdj(λ)`.

If `MDfreq = ω`, where `ω` is a vector of real frequency values, then each distance `dist[i,j]`  is the maximum of pointwise distances evaluated for all frequencies in `ω` and  the corresponding frequency `fpeak[i,j]` is the value for which the maximum pointwise distance is achieved.

The stability boundary offset, `β`, to be used to assess the finite poles/zeros which belong to the boundary of the stability domain can be specified via the keyword parameter `offset = β`. Accordingly, for a continuous-time system, these are the finite poles/zeros having  real parts within the interval `[-β,β]`, while for a discrete-time system,  these are the finite pole/zeros having moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

Pencil reduction algorithms are employed to compute range and coimage spaces involved in evaluating  the ν-gap or the H∞-norm distances. These algorithms perform rank decisions based on rank  revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of the state-space matrices  `Ai`, `Bi`, `Ci`,`Di`, `Aj`, `Bj`, `Cj` and `Dj`, the absolute tolerance for the nonzero elements of `Ei` and `Ej`,    and the relative tolerance for the nonzero elements of all above matrices.   The default relative tolerance is `nij*ϵ`, where `ϵ` is the working machine epsilon  and `nij` is the maximum of the orders of the systems `sysm.sys[i]` and `sysm.sys[j]`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol`, `atol2 = atol`. 

The keyword argument `rtolinf = tol` specifies the relative accuracy `tol` to be used  to compute infinity norms. The default value used is `tol = 0.00001`.

*Method:* The evaluation of ν-gap uses the definition proposed in [1], extended to generalized LTI (descriptor) systems. 

*References:*

[1] G. Vinnicombe. Uncertainty and feedback: H∞ loop-shaping and the ν-gap metric.      Imperial College Press, London, 2001. 
