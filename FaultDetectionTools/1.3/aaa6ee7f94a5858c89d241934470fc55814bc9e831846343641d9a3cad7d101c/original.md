```
mdIFeval(sysQ::MDFilter, sysm::MDMModel; minimal = false, atol, atol1 = atol, atol2 = atol, rtol, fast = true) -> sysR::MDFilterIF
```

Compute the internal form `sysR` of the model detection filter `sysQ` applied to the multiple synthesis model `sysm`.  If the `j`-th component model `sysm.sys[j]` has the partitioned transfer function matrix `Gj(λ) = [ Guj(λ)  Gdj(λ) Gwj(λ) Gvj(λ) ]` in accordance with the partitioned system inputs as `controls`, `disturbances`, `noise` and `auxiliary` inputs, respectively, and `Qi(λ) = [ Qyi(λ) Qui(λ) ]` is the partitioned transfer function matrix of the `i`-th filter `sysQ.sys[i]`  in accordance with the partitioned filter inputs as `outputs` and `controls`, then  the transfer function matrix `Rij(λ)` corresponding to the (`i`-th filter,`j`-th model) pair in the resulting internal form `sysR.sys[i,j]` is given by

```
 Rij(λ) = | Qyi(λ)  Qui(λ) | * | Guj(λ)  Gdj(λ) Gwj(λ) Gvj(λ) |
                               |  I      0      0      0      |
```

Minimal descriptor realizations are computed if `minimal = true` and a (possibly) non-minimal  realization is determined if `minimal = false` (default). 

The minimal realization computation relies on pencil manipulation algorithms which  employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

If `(Arij-λErij,Brij,Crij,Drij)` is the full order descriptor realization of `sysR.sys[i,j]`, then  the keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Arij`, `Brij`, `Crij`, `Drij`, the absolute tolerance for the nonzero elements of `Erij`,   and the relative tolerance for the nonzero elements of `Arij`, `Brij`, `Crij`, `Drij` and `Eirj`. The default relative tolerance is `nij*ϵ`, where `ϵ` is the working *machine epsilon*  and `nij` is the order of the system `sysR.sys[i,j]`.   The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
