```
ChemPotDensitySaturation <: SaturationMethod
ChemPotDensitySaturation(;vl = nothing,
                        vv = nothing,
                        crit = nothing,
                        f_limit = 0.0,
                        atol = 1e-8,
                        rtol = 1e-12,
                        max_iters = 10^4)
```

Saturation method for `saturation_pressure`. It uses equality of Chemical Potentials with a density basis. If no volumes are provided, it will use  [`x0_sat_pure`](@ref).  `vl`  and `vl` are initial guesses for the liquid and vapour volumes. `f_limit`, `atol`, `rtol`, `max_iters` are passed to the non linear system solver.
