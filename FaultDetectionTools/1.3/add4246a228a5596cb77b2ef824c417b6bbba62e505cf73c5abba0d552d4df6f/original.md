```
fdIFeval(sysQ::FDFilter, sysf::FDIModel; minimal = false, atol, atol1 = atol, atol2 = atol, rtol, fast = true) -> sysR::FDFilterIF
```

Compute the internal form `sysR` of the fault detection filter `sysQ` applied to the synthesis model `sysf`.  If `sysf` has the partitioned transfer function matrix `G(λ) = [ Gu(λ)  Gd(λ) Gf(λ) Gw(λ) Gv(λ) ]` in accordance with the partitioned system inputs as `controls`, `disturbances`, `faults`, `noise` and `auxiliary` inputs, respectively, and `Q(λ) = [ Qy(λ) Qu(λ) ]` is the partitioned transfer function matrix of the fault detection filter `sysQ`  in accordance with the partitioned filter inputs as `measurable outputs` and `control inputs`, then  the transfer function matrix `R(λ)` of the resulting internal form `sysR` is given by

```
 R(λ) = | Qy(λ)  Qu(λ) | * | Gu(λ)  Gd(λ) Gf(λ) Gw(λ) Gv(λ) |
                           |  I       0     0     0     0   |
```

A minimal descriptor realization is computed if `minimal = true` and a possibly non-minimal  realization is determined if `minimal = false` (default). 

The minimal realization computation relies on pencil manipulation algorithms which  employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

If `(Ar-λEr,Br,Cr,Dr)` is the full order descriptor realization of `sysR.sys`, then  the keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Ar`, `Br`, `Cr`, `Dr`, the absolute tolerance for the nonzero elements of `Er`,   and the relative tolerance for the nonzero elements of `Ar`, `Br`, `Cr`, `Dr` and `Er`. The default relative tolerance is `nϵ`, where `ϵ` is the working *machine epsilon*  and `n` is the order of the system `sysR`.   The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
