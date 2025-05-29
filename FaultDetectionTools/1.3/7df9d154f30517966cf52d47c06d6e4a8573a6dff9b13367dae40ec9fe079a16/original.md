```
fdIFeval(sysQ::FDIFilter, sysf::FDIModel; minimal = false, atol, atol1 = atol, atol2 = atol, rtol, fast = true) -> sysR::FDIFilterIF
```

Compute the internal form `sysR` of the fault detection and isolation filter `sysQ` applied to the synthesis model `sysf`.  If `sysf` has the partitioned transfer function matrix `G(λ) = [ Gu(λ)  Gd(λ) Gf(λ) Gw(λ) Gv(λ) ]` in accordance with the partitioned system inputs as `controls`, `disturbances`, `faults`, `noise` and `auxiliary` inputs, respectively, and `Qi(λ) = [ Qyi(λ) Qui(λ) ]` is the partitioned transfer function matrix of the `i`-th filter `sysQ.sys[i]`  in accordance with the partitioned filter inputs as `measurable outputs` and `control inputs`, then  the transfer function matrix `Ri(λ)` of the `i`-th filter in the resulting internal form `sysR.sys[i]` is given by

```
 Ri(λ) = | Qyi(λ)  Qui(λ) | * | Gu(λ)  Gd(λ) Gf(λ) Gw(λ) Gv(λ) |
                              |  I       0     0     0     0   |
```

Minimal descriptor realizations are computed if `minimal = true` and a possibly non-minimal  realization is determined if `minimal = false` (default). 

The minimal realization computation relies on pencil manipulation algorithms which  employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

If `(Ari-λEri,Bri,Cri,Dri)` is the full order descriptor realization of `sysR.sys[i]`, then  the keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Ari`, `Bri`, `Cri`, `Dri`, the absolute tolerance for the nonzero elements of `Eri`,   and the relative tolerance for the nonzero elements of `Ari`, `Bri`, `Cri`, `Dri` and `Eir`. The default relative tolerance is `ni*ϵ`, where `ϵ` is the working *machine epsilon*  and `ni` is the order of the system `sysR.sys[i]`.   The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
