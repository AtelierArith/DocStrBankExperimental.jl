```
ChemPotVSaturation <: SaturationMethod
ChemPotVSaturation(V0)
ChemPotVSaturation(;vl = nothing,
                    vv = nothing,
                    crit = nothing,
                    crit_retry = true
                    f_limit = 0.0,
                    atol = 1e-8,
                    rtol = 1e-12,
                    max_iters = 10^4)
```

Default `saturation_pressure` Saturation method used by `Clapeyron.jl`. It uses equality of Chemical Potentials with a volume basis. If no volumes are provided, it will use  [`x0_sat_pure`](@ref). If those initial guesses fail and the specification is near critical point, it will try one more time, using Corresponding States instead. when `crit_retry` is true, if the initial solve fail, it will try to obtain a better estimate by calculating the critical point. `f_limit`, `atol`, `rtol`, `max_iters` are passed to the non linear system solver.
