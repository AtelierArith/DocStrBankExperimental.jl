```
 γ = fdimmperf(sysr::FDFilterIF, SFDI[, nrmflag])
```

Compute the model-matching performance `γ` of the fault detection filter internal form object `sysr::FDFilterIF` for a given binary structure vector `SFDI`. If `Rf(λ)` is the transfer function matrix of the  transfer channel from the fault inputs to residuals `sysr.sys[:,sysr.faults]` and  `Rw(λ)` is the transfer function matrix of the transfer channel from the noise inputs to residuals  `sysr.sys[:,sysr.noise]`, then `γ` is the  H∞-norm of `[Rdf(λ) Rw(λ)]`, if `nrmflag = Inf` (default) and the  H2-norm of `[Rdf(λ) Rw(λ)]`,  if `nrmflag = 2`, where `Rdf(λ)` is the transfer function matrix formed by those `j`-th columns of `Rf(λ)` for which  `SFDI[j] = 0`.   The value of `γ` is infinite for an unstable filter or if `nrmflag = 2` and the transfer function matrix `[Rdf(λ) Rw(λ)]` of a continuous-time system is not strictly proper.
