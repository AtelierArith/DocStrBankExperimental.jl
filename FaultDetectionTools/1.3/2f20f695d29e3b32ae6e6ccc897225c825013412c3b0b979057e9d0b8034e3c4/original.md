```
 fdif2ngap(sysr::FDFilterIF, freq) -> (gap, β, γ)
```

Compute the fault-to-noise gap `gap` (and the related quantities `β` and `γ`)  for the stable fault detection filter internal form object `sysr::FDFilterIF`. For the fault to residual channel of the filter `sysr.sys[:,sysr.faults]`    with the corresponding transfer function matrix `Rf(λ)` and  the noise to residual channel of the filter `sysr.sys[:,sysr.noise]`    with the corresponding transfer function matrix `Rw(λ)`,     `β` is the H∞- index of `Rf(λ)`, `γ` is the H∞-norm of `Rw(λ)` and  `gap` is the fault-to-noise gap evaluated as `gap := β/γ`.  If `freq` is a vector of real frequency values, then `β` and `γ` are evaluated over the frequencies contained in `freq`.  `gap = ∞` if there are no noise inputs and `gap = 0` if there are no fault inputs.
