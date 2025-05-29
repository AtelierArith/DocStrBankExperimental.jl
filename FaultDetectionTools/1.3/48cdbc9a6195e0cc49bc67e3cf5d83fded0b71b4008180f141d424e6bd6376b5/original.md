```
 γ = fdimmperf(sysr::FDFilterIF[, nrmflag])
```

Compute the model-matching performance `γ` of the fault detection filter internal form object `sysr::FDFilterIF`.  If `Rw(λ)` is the transfer function matrix of the transfer channel from the noise inputs to residuals  `sysr.sys[:,sysr.noise]`, then `γ` is the  H∞-norm of `Rw(λ)`, if `nrmflag = Inf` (default) and the  H2-norm of `Rw(λ)`, if `nrmflag = 2`. The value of `γ` is infinite for an unstable filter or if `nrmflag = 2` and the transfer function matrix `Rw(λ)` of a continuous-time system is not strictly proper.
