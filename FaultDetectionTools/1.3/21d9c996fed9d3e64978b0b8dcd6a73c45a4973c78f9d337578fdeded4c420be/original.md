```
 γ = fdimmperf(sysr::FDIFilterIF[, nrmflag])
```

Compute the model-matching performance `γ` of the stable fault detection and isolation filter internal form object `sysr::FDIFilterIF`.  The filter `sysr` consists of `N` individual FDI filters `sysr.sys[i]`, for `i = 1, ..., N`, where `sysr.sys[i][:,sysr.noise]` is the noise to residual channel of the `i`-th filter  with the corresponding transfer function matrix `Rwi(λ)`. Then,  `γ` is an `N`-dimensional vector whose `i`-th component is the  H∞-norm of `Rwi(λ)`, if `nrmflag = Inf` (default)  and the  H2-norm of `Rwi(λ)`, if `nrmflag = 2`. The `i`-th component of `γ` is infinite for an unstable filter or if `nrmflag = 2` and the transfer function matrix `Rwi(λ)` of a continuous-time system is not strictly proper.
