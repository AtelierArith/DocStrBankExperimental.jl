```
mdmatch(sysQ::MDFilter, sysc::MDModel; MDfreq, minimal = false, rtolinf, offset, atol, atol1 = atol, atol2 = atol, rtol, fast = true) -> (mdgain,fpeak,mind)
```

Compute the distance-mapping performance vector `mdgain` achieved using the model detection filter object `sysQ::MDFilter` applied to a component model `sysc::MDModel`, the corresponding vector of peak frequencies `fpeak`, and the index `mind` of the component of `mdgain` for which the minimum gain value is achieved. 

If the `i`-th filter `sysQ.sys[i]` has the transfer function matrix `Qi(λ)` and  the component model `sysc::MDModel` has the partitioned transfer function matrix  `G(λ) = [Gu(λ)  Gd(λ) Gw(λ) Gv(λ)]` in accordance with the partitioned system inputs as `controls`, `disturbances`, `noise` and `auxiliary` inputs, respectively, then the distance-mapping performance of the `i`-th filter applied to the given component model is computed as  `mdgain[i] = || Ri(λ) ||∞`, where `Ri(λ)`  is the corresponding internal form

```
 Ri(λ) = Qi(λ) * | Gu(λ)  Gd(λ) Gw(λ) Gv(λ) | .
                 |  I     0     0     0     |
```

Minimal descriptor realizations are computed for `Ri(λ)` if `minimal = true` and a (possibly) non-minimal  realization is determined if `minimal = false` (default). 

The computation of minimal realizations of individual input-output channels relies on pencil manipulation algorithms, which employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true` (default) or  the more reliable SVD-decompositions if `fast = false`.

If `(Ari-λEri,Bri,Cri,Dri)` is the full order descriptor realization of `Ri(λ)`, then  the keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Ari`, `Bri`, `Cri`, `Dri`, the absolute tolerance for the nonzero elements of `Eri`,   and the relative tolerance for the nonzero elements of `Ari`, `Bri`, `Cri`, `Dri` and `Eir`. The default relative tolerance is `ni*ϵ`, where `ϵ` is the working *machine epsilon*  and `ni` is the order of the realitation of `Ri(λ)`.   The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
