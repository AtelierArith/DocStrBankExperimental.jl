```
AntoineSaturation <: SaturationMethod
AntoineSaturation(;T0 = nothing,
                    vl = nothing,
                    vv = nothing,
                    f_limit = 0.0,
                    atol = 1e-8,
                    rtol = 1e-12,
                    max_iters = 10^4,
                    crit = nothing,
                    crit_retry = false)
```

Saturation method for `saturation_temperature` .Default method for saturation temperature from Clapeyron 0.3.7. It solves the Volume-Temperature system of equations for the saturation condition.

If only `T0` is provided, `vl` and `vv` are obtained via [`x0_sat_pure`](@ref). If `T0` is not provided, it will be obtained via [`x0_saturation_temperature`](@ref). It is recommended to overload `x0_saturation_temperature`, as the default starting point calls [`crit_pure`](@ref), resulting in slower than ideal times. `f_limit`, `atol`, `rtol`, `max_iters` are passed to the non linear system solver.
