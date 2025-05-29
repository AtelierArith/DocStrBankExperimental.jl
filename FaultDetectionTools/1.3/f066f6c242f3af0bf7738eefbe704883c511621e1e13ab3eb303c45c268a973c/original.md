```
 fdiscond(sysr::FDFilterIF,freq) -> (scond, β, γ)
```

Compute for the stable transfer function matrix `Rf(λ)` of the transfer channel from the fault inputs to residuals of the fault detection filter internal form object `sysr::FDFilterIF` the quantities:  `β` - the H∞- index of `Rf(λ)`, `γ` - the maximum of the columns norms of `Rf(λ)` and  the fault detection sensitivity condition `scond` evaluated as `scond := β/γ`.  If `freq` is a vector of real frequency values, then `β` and `γ` are evaluated over the frequencies contained in `freq`. 
