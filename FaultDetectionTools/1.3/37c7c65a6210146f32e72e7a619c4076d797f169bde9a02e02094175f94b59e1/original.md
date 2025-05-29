```
 fdiscond(sysr::FDFilterIF,SFDI,freq) -> (scond, β, γ)
```

Compute the detection and isolation sensitivity condition `scond` (and related quatities `β` and `γ`) for the binary structure vector `SFDI` associated to the stable transfer function matrix `Rf(λ)` of the transfer channel from the fault inputs to residuals of the fault detection filter internal form object `sysr::FDFilterIF`.  If  `Rff(λ)` is the transfer function matrix formed of those `j`-th columns of `Rf(λ)`  for which `SFDI[j] = 1`, then:    `β` - the H∞- index of `Rff(λ)`, `γ` - the maximum of the columns norms of `Rff(λ)` and  the fault detection sensitivity condition `scond` evaluated as `scond := β/γ`.  If `freq` is a vector of real frequency values, then `β` and `γ` are evaluated over the frequencies contained in `freq`. 
